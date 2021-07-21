# API概览

配置审计提供以下API。

## 普通账号的合规包

|API|描述|
|---|--|
|[CreateCompliancePack]()|调用CreateCompliancePack接口创建合规包。|
|[ListCompliancePacks]()|调用ListCompliancePacks接口查询合规包列表。|
|[GetCompliancePack]()|调用GetCompliancePack接口查询合规包详情。|
|[UpdateCompliancePack]()|调用UpdateCompliancePack接口修改合规包信息。|
|[DeleteCompliancePacks]()|调用DeleteCompliancePacks接口删除合规包。|
|[GenerateCompliancePackReport]()|调用GenerateCompliancePackReport接口生成合规包的评估报告。|
|[GetCompliancePackReport]()|调用GetCompliancePackReport接口查询合规包的评估报告。|
|[GetConfigRuleComplianceByPack]()|调用GetConfigRuleComplianceByPack接口查询合规包中规则的合规结果。|
|[GetResourceComplianceByPack]()|调用GetResourceComplianceByPack接口查询合规包中资源的合规结果。|

## 普通账号的规则

|API|描述|
|---|--|
|[CreateConfigRule]()|调用CreateConfigRule接口创建规则。|
|[UpdateConfigRule]()|调用UpdateConfigRule接口修改规则。|
|[GetConfigRule]()|调用GetConfigRule接口查询指定规则详情。|
|[DeactiveConfigRules]()|调用DeactiveConfigRules接口停用规则。|
|[ListResourceEvaluationResults]()|调用ListResourceEvaluationResults接口查询资源评估结果。|
|[ListConfigRuleEvaluationResults]()|调用ListConfigRuleEvaluationResults接口查询规则对资源的评估结果。|
|[GenerateConfigRulesReport]()|调用GenerateConfigRulesReport接口生成规则列表中所有规则的评估报告。|
|[GetConfigRulesReport]()|调用GetConfigRulesReport接口查询规则列表中所有规则的评估报告。|
|[GetResourceComplianceByConfigRule]()|调用GetResourceComplianceByConfigRule接口查询规则对资源的评估结果。|
|[GetConfigRuleSummaryByRiskLevel]()|调用GetConfigRuleSummaryByRiskLevel接口查询不同风险等级规则的合规概要。|

## 普通账号的资源

|API|描述|
|---|--|
|[GetDiscoveredResourceCountsGroupByRegion]()|调用GetDiscoveredResourceCountsGroupByRegion接口从地域维度查询资源的统计结果。|
|[GetDiscoveredResourceCountsGroupByResourceType]()|调用GetDiscoveredResourceCountsGroupByResourceType接口从资源类型维度查询资源的统计结果。|
|[GetResourceConfigurationTimeline]()|调用GetResourceConfigurationTimeline接口查询指定资源的配置时间线。|
|[GetResourceComplianceTimeline]()|调用GetResourceComplianceTimeline接口查询指定资源的合规时间线。|

## 企业管理账号的账号组

|API|描述|
|---|--|
|[CreateAggregator]()|调用CreateAggregator接口创建账号组。|
|[ListAggregators]()|调用ListAggregators接口查询账号组列表。|
|[GetAggregator]()|调用GetAggregator接口查询账号组详情。|
|[UpdateAggregator]()|调用UpdateAggregator接口更新账号组的配置。|
|[DeleteAggregators]()|调用DeleteAggregators接口删除账号组。|

## 企业管理账号的合规包

|API|描述|
|---|--|
|[ListCompliancePackTemplates]()|调用ListCompliancePackTemplates接口查询合规包模板列表。|
|[CreateAggregateCompliancePack]()|调用CreateAggregateCompliancePack接口为指定账号组创建合规包。|
|[ListAggregateCompliancePacks]()|调用ListAggregateCompliancePacks接口查询指定账号组内的合规包列表。|
|[GetAggregateCompliancePack]()|调用GetAggregateCompliancePack接口查询指定账号组内合规包详情。|
|[UpdateAggregateCompliancePack]()|调用UpdateAggregateCompliancePack接口修改指定账号组内的合规包信息。|
|[DeleteAggregateCompliancePacks]()|调用DeleteAggregateCompliancePacks接口删除指定账号组内的合规包。|
|[GenerateAggregateCompliancePackReport]()|调用GenerateAggregateCompliancePackReport接口为指定账号组内的指定合规包生成评估报告。|
|[GetAggregateCompliancePackReport]()|调用GetAggregateCompliancePackReport接口查询指定账号组内指定合规包的评估报告。|
|[GetAggregateResourceComplianceByPack]()|调用GetAggregateResourceComplianceByPack接口查询指定账号组内指定合规包中资源的合规结果。|
|[GetAggregateConfigRuleComplianceByPack]()|调用GetAggregateConfigRuleComplianceByPack接口查询指定账号组内指定合规包中规则的合规结果。|
|[GetAggregateAccountComplianceByPack]()|调用GetAggregateAccountComplianceByPack接口查询指定账号组内指定合规包中成员账号的合规结果。|

## 企业管理账号的规则

|API|描述|
|---|--|
|[CreateAggregateConfigRule]()|调用CreateAggregateConfigRule接口为指定账号组创建规则。|
|[ListAggregateConfigRules]()|调用ListAggregateConfigRules接口查询指定账号组内的规则列表。|
|[GetAggregateConfigRule]()|调用GetAggregateConfigRule接口查询指定账号组内指定规则详情。|
|[UpdateAggregateConfigRule]()|调用UpdateAggregateConfigRule接口修改指定账号组内的规则。|
|[DeleteAggregateConfigRules]()|调用DeleteAggregateConfigRules接口删除指定账号组内的规则。|
|[ActiveAggregateConfigRules]()|调用ActiveAggregateConfigRules接口启用指定账号组内的规则。|
|[DeactiveAggregateConfigRules]()|调用DeactiveAggregateConfigRules接口停用指定账号组内的规则。|
|[GenerateAggregateConfigRulesReport]()|调用GenerateAggregateConfigRulesReport接口为指定账号组内规则列表中的所有规则生成评估报告。|
|[GetAggregateConfigRulesReport]()|调用GetAggregateConfigRulesReport接口查询指定账号组内规则列表中所有规则的评估报告。|
|[StartAggregateConfigRuleEvaluation]()|调用StartAggregateConfigRuleEvaluation接口使指定账号组内的规则执行一次评估。|
|[GetAggregateResourceComplianceByConfigRule]()|调用GetAggregateResourceComplianceByConfigRule接口查询指定账号组内规则对资源的评估结果。|
|[GetAggregateConfigRuleSummaryByRiskLevel]()|调用GetAggregateConfigRuleSummaryByRiskLevel接口查询指定账号组内不同风险等级规则的合规概要。|
|[ListAggregateConfigRuleEvaluationResults]()|调用ListAggregateConfigRuleEvaluationResults接口查询指定账号组内规则对资源的评估结果。|
|[ListAggregateResourceEvaluationResults]()|调用ListAggregateResourceEvaluationResults接口查询指定账号组内资源的评估结果。|

## 企业管理账号的资源

|API|描述|
|---|--|
|[GetAggregateResourceCountsGroupByResourceType]()|调用GetAggregateResourceCountsGroupByResourceType接口从资源类型维度查询指定账号组内资源的统计结果。|
|[GetAggregateResourceCountsGroupByRegion]()|调用GetAggregateResourceCountsGroupByRegion接口从地域维度查询指定账号组内资源的统计结果。|
|[GetAggregateResourceConfigurationTimeline]()|调用GetAggregateResourceConfigurationTimeline接口查询指定账号组内指定资源的配置时间线。|
|[GetAggregateResourceComplianceTimeline]()|调用GetAggregateResourceComplianceTimeline接口查询指定账号组内指定资源的合规时间线。|

