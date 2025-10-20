<createTable tableName="PRODUCT_GROUP" schemaName="WORKBENCH_DATA">
    <column name="ID" type="UUID">
        <constraints primaryKey="true" nullable="false" unique="true"/>
    </column>
    <column name="VERSION" type="INT"/>
    <column name="EDIT_DATE" type="TIMESTAMP WITH TIME ZONE"/>
    <column name="LABEL" type="VARCHAR(255)"/>
    <column name="DISPLAY_NAME" type="VARCHAR(255)"/>
    <column name="DISPLAY_TYPE" type="VARCHAR(255)"/>
    <column name="DISPLAY_SIZE" type="VARCHAR(255)"/>
    <column name="IS_COLLAPSED" type="BOOLEAN" defaultValue="false"/>
    <column name="IS_DISPLAYED_PRIMARY" type="BOOLEAN" defaultValue="true"/>
    <column name="IS_GROUP_INTERSECTION_LOGIC_IGNORE" type="BOOLEAN" defaultValue="true"/>
    <column name="ABSTRACT_SETTINGS" type="JSONB" defaultValue="{}"/>
    <column name="PRODUCT_GROUP_ITEMS" type="JSONB" defaultValue="{}"/>
</createTable>


<createTable tableName="ABSTRACT_SETTINGS" schemaName="WORKBENCH_DATA">
    <column name="ID" type="UUID">
        <constraints primaryKey="true" nullable="false" unique="true"/>
    </column>
    <column name="VERSION" type="INT"/>
    <column name="TYPE" type="VARCHAR(255)"/>
    <column name="SUBTYPE" type="VARCHAR(255)"/>
    <column name="RULE" type="JSONB" defaultValue="{}"/>
    <column name="VALUE" type="JSONB" defaultValue="{}"/>
    
    <!-- внешний ключ на PRODUCT_GROUP -->
    <column name="PRODUCT_GROUP_ID" type="UUID">
        <constraints nullable="false"
                     foreignKeyName="FK_ABSTRACT_SETTINGS_PRODUCT_GROUP"
                     references="WORKBENCH_DATA.PRODUCT_GROUP(ID)"/>
    </column>
</createTable>