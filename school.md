#include <string.h>
#include <stdlib.h>
#include <mysql/mysql.h>
#include "cgic.h"

int cgiMain()
{

	fprintf(cgiOut, "Content-type:text/html;charset=utf-8\n\n");

	char Sname[20] = "\0";
	char Sdept[5] = "\0";
	char Sdname[20]= "\0";
	int status = 0;

	status = cgiFormString("Sname",  Sname, 20);
	if (status != cgiFormSuccess)
	{
		fprintf(cgiOut, "get Sname error!\n");
		return 1;
	}

	status = cgiFormString("Sdept",  Sdept, 5);
	if (status != cgiFormSuccess)
	{
		fprintf(cgiOut, "get Sdept error!\n");
		return 1;
	}

	status = cgiFormString("Sdname",  Sdname, 20);
	if (status != cgiFormSuccess)
	{
		fprintf(cgiOut, "get Sdname error!\n");
		return 1;
	}





	//fprintf(cgiOut, "name = %s, age = %s, stuId = %s\n", name, age, stuId);

	//int ret;
	char sql[128] = "\0";
	MYSQL *db;

	//初始化
	db = mysql_init(NULL);
	mysql_options(db,MYSQL_SET_CHARSET_NAME,"utf8");
	if (db == NULL)
	{
		fprintf(cgiOut,"mysql_init fail:%s\n", mysql_error(db));
		return -1;
	}

	//连接数据库
	db = mysql_real_connect(db, "127.0.0.1", "root", "123456", "stu",  3306, NULL, 0);
	if (db == NULL)
	{
		fprintf(cgiOut,"mysql_real_connect fail:%s\n", mysql_error(db));
		mysql_close(db);
		return -1;
	}



	/*strcpy(sql, "create table information(Ino CHAR(20) PRIMARY KEY,
 Iname CHAR(20) NOT NULL,
   Isex CHAR(2) CHECK (sex in ('男' ,'女')),
   Iage SMALLINT NOT NULL,
   Iphone  INT(11) UNIQUE NOT NULL,
   Sdept INT,
   FOREIGN KEY (Sdept) REFERENCES school(Sdept))");
	 //创建表，如果=0，创建成功，如果不等于0，表示表已存在，如果不等于1，关闭数据库
	if ((ret = mysql_real_query(db, sql, strlen(sql) + 1)) != 0)
	{
		if (ret != 1)
		{
			fprintf(cgiOut,"mysql_real_query fail:%s\n", mysql_error(db));
			mysql_close(db);
			return -1;
		}
	} */



	sprintf(sql, "insert into school values('%s', '%s','%s')",Sname,Sdept,Sdname);
	if (mysql_real_query(db, sql, strlen(sql) + 1) != 0)
	{
		fprintf(cgiOut, "%s\n", mysql_error(db));
		mysql_close(db);
		return -1;
	}

	fprintf(cgiOut, "add school ok!\n");
	mysql_close(db);
	return 0;
}
