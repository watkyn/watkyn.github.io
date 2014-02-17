---
layout: post
title: "Using sqlite3 in a Visual Studio 2008 C++ application"
date: 2008-07-09 09:14:36 -0600
comments: true
categories: c++
---


I had a terrible time finding out how to get sqlite working with VC++ using the windows binaries from the sqlite download page. Most of the trouble was from me being a complete newb to VC++ but in the end I got it working. Here are the steps to follow along for next time.

1. Download the precompiled binaries for Windows and also download the source code.
2. The DLL download should contain the following files: sqlite3.dll and sqlite3.def
3. The source code should contain lots of c code and header files, you need to find the sqlite3.h header file.
4. Put sqlite3.dll, sqlite3.def, and sqlite3.h files into a directory somewhere.
5. Next you need to create a sqlite3.lib file in order to implicitly link the dll to your project
- From the command line, navigate to the folder that has the sqlite3 files from step 4, then type the following:
- LIB /DEF:sqlite3.def
- This should create two more files: sqlite3.lib and sqlite3.exp
- NOTE: LIB.exe needs to be on your path and can be found it in the Visual Studio install directory (do a search).
6. Now start a new console application project in Visual Studio
7. Copy the sqlite3.dll, sqlite3.lib, and sqlite3.h files into your new project directory
8. Right click on the Resource Files folder and choose Add >> Existing Item ... then choose sqlite3.lib
9. You may get a dialog that asks you about the custom rule, I just chose no.
10. Now add the sqlite3.h file into your project headers directory in Visual Studio (project >> Add >> Existing item)
11. Now you should be able to start using sqlite3: Here is a sample console app you can try.
12. This will create a new db and a sample table and spit out a resultset to the console.

``` c++ Junk
#include "stdafx.h"
#include "sqlite3.h"

static int callback(void *NotUsed, int argc, char **argv, char **azColName) {
int i;
for(i=0; i<argc; i++){
printf("%s = %s\n", azColName[i], argv[i] ? argv[i] : "NULL");
}
printf("\n");
return 0;
}


int _tmain(int argc, _TCHAR* argv[]) {
sqlite3 *db;
char *zErrMsg = 0;
int rc;

rc = sqlite3_open("test.db", &db);
if( rc ) {
fprintf(stderr, "Can't open database: %s\n", sqlite3_errmsg(db));
sqlite3_close(db);
return 1;
}
rc = sqlite3_exec(db, "create table stuff ( name )", callback, 0, &zErrMsg);
rc = sqlite3_exec(db, "insert into stuff values ('hello')", callback, 0, &zErrMsg);
rc = sqlite3_exec(db, "select * from stuff", callback, 0, &zErrMsg);
if(rc != SQLITE_OK) {
fprintf(stderr, "SQL error: %s\n", zErrMsg);
sqlite3_free(zErrMsg);
}
sqlite3_close(db);
return 0;
}
```