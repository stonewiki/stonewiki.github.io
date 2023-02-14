---
title: XML高级映射
toc: false
date: 2023-02-14 23:04:48
tags: [Mybatis]
---

#### 映射一对多，多中嵌套一对一
``` xml
<resultMap id="tkDetailCdCompleteMap" type="com.gc.tkdms.form.vo.TkDetailCdCompleteVO">
        <result column="APPLY_ID" jdbcType="VARCHAR" property="id"/>
        <result column="CREATE_TIME" jdbcType="TIMESTAMP" property="createTime"/>
        <result column="APPLY_TITLE" jdbcType="VARCHAR" property="applyTitle"/>

        <collection property="tkDetailCdBasic" ofType="com.gc.tkdms.form.vo.TkDetailCdBasicVO">
            <id column="basicId" jdbcType="VARCHAR" property="id" />
            <result column="bCreateBy" jdbcType="VARCHAR" property="createBy" />
            <result column="bCreateTime" jdbcType="TIMESTAMP" property="createTime" />
            <result column="bUpdateBy" jdbcType="VARCHAR" property="updateBy" />
            <result column="bUpdateTime" jdbcType="TIMESTAMP" property="updateTime" />
            <result column="DOUBLE_CHECK" jdbcType="VARCHAR" property="doubleCheckId" />
            <association property="doubleCheck" javaType="com.gc.tkdms.form.vo.ComponentEmpVO" resultMap="doubleCheckEmpMap">
            </association>

        </collection>
        <collection property="tkDetailCdMaskMappings" ofType="com.gc.tkdms.form.entity.TkDetailCdMaskMapping">
            <id column="mappingId" jdbcType="VARCHAR" property="id" />
            <result column="mCreateBy" jdbcType="VARCHAR" property="createBy" />
            <result column="mCreateTime" jdbcType="TIMESTAMP" property="createTime" />
            <result column="mUpdateBy" jdbcType="VARCHAR" property="updateBy" />
            <result column="mUpdateTime" jdbcType="TIMESTAMP" property="updateTime" />
        </collection>
</resultMap>
```

``` xml
<resultMap id="doubleCheckEmpMap" type="com.gc.tkdms.form.vo.ComponentEmpVO">
        <id column="emp_id" jdbcType="VARCHAR" property="id" />
        <result column="emp_id" jdbcType="VARCHAR" property="username" />
        <result column="REALNAME" jdbcType="VARCHAR" property="realname" />
        <result column="DISPLAYNAME" jdbcType="VARCHAR" property="displayName" />
</resultMap>
```