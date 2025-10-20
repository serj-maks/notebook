# notebook
notebook

описал таблицу product_group для liquibase
```xml
<?xml version="1.0" encoding="UTF-8"?>

<databaseChangeLog
        xmlns="http://www.liquibase.org/xml/ns/dbchangelog"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://www.liquibase.org/xml/ns/dbchangelog
                      http://www.liquibase.org/xml/ns/dbchangelog/dbchangelog-4.9.xsd">

    <changeSet id="0057-add-product-group-table" author="23276228">
        <preConditions onFail="MARK_RAN">
            <and>
                <not>
                    <tableExists tableName="PRODUCT_GROUP" schemaName="WORKBENCH_DATA"/>
                </not>
            </and>
        </preConditions>

        <createTable tableName="PRODUCT_GROUP" schemaName="WORKBENCH_DATA">
            <column name="ID" type="UUID">
                <constraints primaryKey="true" nullable="false" unique="true"/>
            </column>
            <column name="VERSION" type="INT"/>
            <column name="EDIT_DATE" type="JAVA.SQL.TYPES.TIMESTAMP_WITH_TIMEZONE"/>
            <column name="LABEL" type="VARCHAR(255)"/>
            <column name="DISPLAY_NAME" type="VARCHAR(255)"/>
            <column name="DISPLAY_TYPE" type="VARCHAR(255)"/>
            <column name="DISPLAY_SIZE" type="VARCHAR(255)"/>
            <column name="IS_COLLAPSED" type="boolean" defaultValue="false"/>
            <column name="IS_DISPLAYED_PRIMARY" type="boolean" defaultValue="true"/>
            <column name="IS_GROUP_INTERSECTION_LOGIC_IGNORE" type="boolean" defaultValue="true"/>
            <column name="ABSTRACT_SETTINGS" type="JSONB" defaultValue="{}"/>
            <column name="PRODUCT_GROUP_ITEMS" type="JSONB" defaultValue="{}"/>
        </createTable>
    </changeSet>

</databaseChangeLog>
```

так же описал таблицу abstract_settings
```xml
<?xml version="1.0" encoding="UTF-8"?>

<databaseChangeLog
        xmlns="http://www.liquibase.org/xml/ns/dbchangelog"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://www.liquibase.org/xml/ns/dbchangelog
                      http://www.liquibase.org/xml/ns/dbchangelog/dbchangelog-4.9.xsd">

    <changeSet id="0059-add-abstract-settings-table" author="23276228">
        <preConditions onFail="MARK_RAN">
            <and>
                <not>
                    <tableExists tableName="ABSTRACT_SETTINGS" schemaName="WORKBENCH_DATA"/>
                </not>
            </and>
        </preConditions>

        <createTable tableName="ABSTRACT_SETTINGS" schemaName="WORKBENCH_DATA">
            <column name="ID" type="UUID">
                <constraints primaryKey="true" nullable="false" unique="true"/>
            </column>
            <column name="VERSION" type="INT"/>
            <column name="TYPE" type="VARCHAR(255)"/>
            <column name="SUBTYPE" type="VARCHAR(255)"/>
            <column name="RULE" type="JSONB" defaultValue="{}"/>
            <column name="VALUE" type="JSONB" defaultValue="{}"/>
        </createTable>
    </changeSet>

</databaseChangeLog>
```

нужно сделать связь один-ко-многим. Т.е. у одного product_group будет несколько abstract_settings. По идее, нужно сделать в таблице product_group ссылку на abstract_settings (какой-нибудь abstract_settings_id) или наоборот ?
