<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>学生课程管理系统</title>
    <link rel="stylesheet" type="text/css" href="./public/css/bootstrap.min.css">
    <style type="text/css">
    body {
        height: 100%;
        background-color: lightblue;
    }
    ul li {
    	list-style: none;
    }
    
    .header {
        margin-bottom: 50px;
    }
    
    .operation>div {
        padding: 15px;
    }
    .operation.row .text-center button {
    	outline-style: none;
    }
    
    .forms li {
        display: none;
    }
    
    .forms li button {
        margin-right: 30px;
    }
    </style>
</head>

<body>
    <h1 class="header text-center">学生课程管理系统</h1>
    <div class="container">
        <div class="operation row">
            <div class="text-center col-md-3 col-sm-6">
                <button>添加课程信息</button>
            </div>
            <div class="text-center col-md-3 col-sm-6">
                <button>查询课程信息</button>
            </div>
            <div class="text-center col-md-3 col-sm-6">
                <button>修改课程信息</button>
            </div>
            <div class="text-center col-md-3 col-sm-6">
                <button>删除课程信息</button>
            </div>
        </div>
        <ul class="forms">
            <li class="show">
                <form class="form-horizontal" method="get" action="/cgi-bin/sx/addcourse.cgi">
                    <div class="form-group">
                        <label for="Cno" class="col-sm-2 control-label">课程编号</label>
                        <div class="col-sm-10">
                            <input type="text" name="Cno" class="form-control" id="Cno" placeholder="请输入课程编号">
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="Cname" class="col-sm-2 control-label">课程名称</label>
                        <div class="col-sm-10">
                            <input type="text" name="Cname" class="form-control" id="Cname" placeholder="请输入课程名称">
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="Ccredit" class="col-sm-2 control-label">课程学分</label>
                        <div class="col-sm-10">
                            <input type="text" name="Ccredit" class="form-control" id="Ccredit" placeholder="请输入课程学分">
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="Cpno" class="col-sm-2 control-label">先修课</label>
                        <div class="col-sm-10">
                            <input type="text" name="Cpno" class="form-control" id="Cpno" placeholder="请输入先修课，可为空">
                        </div>
                    </div>
                    <div class="text-center">
                        <button type="submit" class="btn btn-success">提交</button>
                        <button type="reset" class="btn btn-success">重置</button>
                    </div>
                </form>
            </li>
            <li>
                <form class="form-horizontal" method="get" action="/cgi-bin/sx/selcourse.cgi">
                    <div class="form-group">
                        <label for="name-sel" class="col-sm-2 control-label">输入课程号查询</label>
                        <div class="col-sm-10">
                            <input type="text" name="Cno" class="form-control" id="Cno-sel" placeholder="输入*查询所有">
                        </div>
                    </div>
                    <div class="text-center">
                        <button type="submit" class="btn btn-success">提交</button>
                        <button type="reset" class="btn btn-success">重置</button>
                    </div>
                </form>
            </li>
            <li>
                <form class="form-horizontal" method="get" action="/cgi-bin/sx/modcourse.cgi">
                    <div class="form-group">
                        <label for="Cno-mod" class="col-sm-2 control-label">课程编号</label>
                        <div class="col-sm-10">
                            <input type="text" name="Cno" class="form-control" id="Cno-mod" placeholder="请输入课程编号">
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="Cname-mod" class="col-sm-2 control-label">课程名称</label>
                        <div class="col-sm-10">
                            <input type="text" name="Cname" class="form-control" id="Cname-mod" placeholder="请输入课程名称">
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="Ccredit-mod" class="col-sm-2 control-label">课程学分</label>
                        <div class="col-sm-10">
                            <input type="text" name="Ccredit" class="form-control" id="Ccredit-mod" placeholder="请输入课程学分">
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="Cpno-mod" class="col-sm-2 control-label">先修课</label>
                        <div class="col-sm-10">
                            <input type="text" name="Cpno" class="form-control" id="Cpno-mod" placeholder="请输入先修课，可为空">
                        </div>
                    </div>
                    <div class="text-center">
                        <button type="submit" class="btn btn-success">提交</button>
                        <button type="reset" class="btn btn-success">重置</button>
                    </div>
                </form>
            </li>
            <li>
                <form class="form-horizontal" method="get" action="/cgi-bin/sx/del.cgi">
                    <div class="form-group">
                        <label for="Cno-del" class="col-sm-2 control-label">输入要删除的课程编号</label>
                        <div class="col-sm-10">
                            <input type="text" name="Cno" class="form-control" id="Cno-del" placeholder="输入课程编号">
                        </div>
                    </div>
                    <div class="text-center">
                        <button type="submit" class="btn btn-success">提交</button>
                        <button type="reset" class="btn btn-success">重置</button>
                    </div>
                </form>
            </li>
        </ul>
    </div>
    <script src="./public/js/jquery-3.0.0.min.js"></script>
    <script src="./public/js/bootstrap.min.js"></script>
    <script type="text/javascript">
    $(function() {
    	var btns = $(".operation button");
    	var lis = $(".forms li");
        btns.addClass("btn btn-primary btn-lg");
        for (var i = 0; i < btns.length; i++){
        	btns.eq(i).click(i, function(event){
        		lis.eq(event.data).addClass("show").siblings().removeClass("show");
        	});
        }
    });
    </script>
</body>

</html>



<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>学生院系管理系统</title>
    <link rel="stylesheet" type="text/css" href="./public/css/bootstrap.min.css">
    <style type="text/css">
    body {
        height: 100%;
        background-color: lightblue;
    }
    ul li {
    	list-style: none;
    }
    
    .header {
        margin-bottom: 50px;
    }
    
    .operation>div {
        padding: 15px;
    }
    .operation.row .text-center button {
    	outline-style: none;
    }
    
    .forms li {
        display: none;
    }
    
    .forms li button {
        margin-right: 30px;
    }
    </style>
</head>

<body>
    <h1 class="header text-center">学生院系管理系统</h1>
    <div class="container">
        <div class="operation row">
            <div class="text-center col-md-3 col-sm-6">
                <button>添加院系信息</button>
            </div>
            <div class="text-center col-md-3 col-sm-6">
                <button>查询院系信息</button>
            </div>
            <div class="text-center col-md-3 col-sm-6">
                <button>修改院系信息</button>
            </div>
            <div class="text-center col-md-3 col-sm-6">
                <button>删除院系信息</button>
            </div>
        </div>
        <ul class="forms">
            <li class="show">
                <form class="form-horizontal" method="get" action="/cgi-bin/sx/addschool.cgi">
                    <div class="form-group">
                        <label for="Sname" class="col-sm-2 control-label">学校名称</label>
                        <div class="col-sm-10">
                            <input type="text" name="Sname" class="form-control" id="Sname" placeholder="请输入学校名称">
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="Sdept" class="col-sm-2 control-label">系编号</label>
                        <div class="col-sm-10">
                            <input type="text" name="Sdept" class="form-control" id="Sdept" placeholder="请输入系编号">
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="Sdname" class="col-sm-2 control-label">系名称</label>
                        <div class="col-sm-10">
                            <input type="text" name="Sdname" class="form-control" id="Sdname" placeholder="请输入系名称">
                        </div>
                    </div>
                    <div class="text-center">
                        <button type="submit" class="btn btn-success">提交</button>
                        <button type="reset" class="btn btn-success">重置</button>
                    </div>
                </form>
            </li>
            <li>
                <form class="form-horizontal" method="get" action="/cgi-bin/sx/selschool.cgi">
                    <div class="form-group">
                        <label for="Sdept-sel" class="col-sm-2 control-label">输入系编号查询</label>
                        <div class="col-sm-10">
                            <input type="text" name="Sdept" class="form-control" id="Sdept-sel" placeholder="输入*查询所有">
                        </div>
                    </div>
                    <div class="text-center">
                        <button type="submit" class="btn btn-success">提交</button>
                        <button type="reset" class="btn btn-success">重置</button>
                    </div>
                </form>
            </li>
            <li>
                <form class="form-horizontal" method="get" action="/cgi-bin/sx/modschool.cgi">
                    <div class="form-group">
                        <label for="Sname-mod" class="col-sm-2 control-label">学校名称</label>
                        <div class="col-sm-10">
                            <input type="text" name="Sname" class="form-control" id="Sname-mod" placeholder="请输入学校名称">
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="Sdept-mod" class="col-sm-2 control-label">系编号</label>
                        <div class="col-sm-10">
                            <input type="text" name="Sdept" class="form-control" id="Sdept-mod" placeholder="请输入系编号">
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="Sdname-mod" class="col-sm-2 control-label">系名称</label>
                        <div class="col-sm-10">
                            <input type="text" name="Sdname" class="form-control" id="Sdname-mod" placeholder="请输入系名称">
                        </div>
                    </div>
                    <div class="text-center">
                        <button type="submit" class="btn btn-success">提交</button>
                        <button type="reset" class="btn btn-success">重置</button>
                    </div>
                </form>
            </li>
            <li>
                <form class="form-horizontal" method="get" action="/cgi-bin/sx/delschool.cgi">
                    <div class="form-group">
                        <label for="Sdept-del" class="col-sm-2 control-label">输入要删除的系编号</label>
                        <div class="col-sm-10">
                            <input type="text" name="Sdept" class="form-control" id="Sdept-del" placeholder="输入系编号">
                        </div>
                    </div>
                    <div class="text-center">
                        <button type="submit" class="btn btn-success">提交</button>
                        <button type="reset" class="btn btn-success">重置</button>
                    </div>
                </form>
            </li>
        </ul>
    </div>
    <script src="./public/js/jquery-3.0.0.min.js"></script>
    <script src="./public/js/bootstrap.min.js"></script>
    <script type="text/javascript">
    $(function() {
    	var btns = $(".operation button");
    	var lis = $(".forms li");
        btns.addClass("btn btn-primary btn-lg");
        for (var i = 0; i < btns.length; i++){
        	btns.eq(i).click(i, function(event){
        		lis.eq(event.data).addClass("show").siblings().removeClass("show");
        	});
        }
    });
    </script>
</body>

</html>




