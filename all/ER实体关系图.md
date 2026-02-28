```mermaid
DROP TABLE IF EXISTS `alarm_result`;
CREATE TABLE `alarm_result`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '告警结果ID',
  `algorithm_id` int NOT NULL COMMENT '所属算法ID，关联 algorithm_ability',
  `inspection_item_id` int NOT NULL COMMENT '检测项ID，关联 algorithm_inspection_items',
  `alarm_rule_id` int NOT NULL COMMENT '触发的告警规则ID，关联 alarm_rule',
  `detection_value` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '实际检测到的值（字符串存储，结合检测项类型解释）',
  `task_result_id` int NOT NULL COMMENT '巡检记录结果id',
  `alarm_level` int NOT NULL COMMENT '告警等级 0:提示 1:一般 2:严重 3:紧急',
  `alarm_message` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '告警说明（可根据规则+检测值生成）',
  `handle_user` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '处理人',
  `handle_result` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '处理结果',
  `status` int NOT NULL DEFAULT 0 COMMENT '告警状态 0:未处理 1:处理中 2:已处理',
  `create_time` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '告警产生时间',
  `update_time` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '告警更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  INDEX `update_time_index`(`update_time` ASC) USING BTREE COMMENT '更新时间索引'
) ENGINE = InnoDB AUTO_INCREMENT = 391 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci ROW_FORMAT = DYNAMIC;
```