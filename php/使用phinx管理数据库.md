# 使用[phinx](https://book.cakephp.org/4/en/phinx/migrations.html)管理数据库

> Phinx通过代码里的php API管理数据迁移,可以解决在不同环境数据库同步问题,也可以追踪到哪些迁移脚本被执行，从而让开发人员更专注于打造更完善的系统。

###### 1. 安装Phinx包   ```composer require robmorgan/phinx```

###### 2. 在项目目录中创建目录db/migrations 

###### 3. 初始化   ```vendor/bin/phinx init```

###### 4. 配置phinx.yml

###### 5. 生成数据迁移   ```php vendor/bin/phinx create MyMigration```

###### 6. 执行数据迁移   ```php vendor/bin/phinx migrate```

###### 7. 常用示例
```
addColumn 增加列
$table = $this->table('phinx_test');
$table->addColumn('create_time', 'integer', ['signed' => false, 'null' => false, 'default' => 0, 'comment' => '创建时间'])
      ->addColumn('update_time', 'integer', ['signed' => false, 'null' => false, 'default' => 0, 'comment' => '编辑时间'])
      ->save();
```

```
editColumn 编辑列
$table = $this->table('phinx_test');
$table->changeColumn('create_time', 'string', ['limit' => 255])
      ->save();
```

```
renameColumn 重命名列
$table = $this->table('phinx_test');
$table->renameColumn('create_time', 'money')
      ->save();
```

```
changeComment 修改表备注
$table = $this->table('phinx_test');
$this->changeComment('服务提供方')
     ->save();
```

```
rename 修改表名
$table = $this->table('phinx_test');
$this->rename('phinx')
     ->save();
```
