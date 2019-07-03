---
title: angular 常规用法
---

1.angular5.0的遍历方式：
``` bash
	第一种：
	ngFor let-bean [ngForOf]="list" let-j="index";
	第二种
	*ngFor="let bean of nzTable.data;
	*ngFor="let data of nzTable.data; index as i;
``` 
2.条件判断

		*ngIf="true"

3.双向数据绑定：[(ngModel)] 是 Angular 的双向数据绑定语法。

		 [(ngModel)]="data"

4：事件绑定

		(click)="event(data)"

5.动态添加class样式。Angular 的 CSS 类绑定机制让根据条件添加或移除一个 CSS 类变得很容易。 只要把 [class.some-css-class]="some-condition" 添加到你要施加样式的元素上就可以了。

	[class.selected]="hero === selectedHero"
	<div [style.display] = "true ? 'block' : 'none'"></div>
6：路由跳转

		import {ActivatedRoute, Router} from '@angular/router';
		constructor(
              public router: Router,
              public route: ActivatedRoute,
             ) {
    super(session, router, route, nzModal, nzTip);
  	}
	this.router.navigate(['/app/base/contract_mapping_list', orgId]);// 后面接传的差数
	// 获得路由上面携带的参数
	this.route.params.subscribe((params: any) => {
	//params 即路由上面的参数
      this.submit_detail(params['id']);
      this.fromUrlId = params.id
    });

7.angular内置过滤器（https://blog.csdn.net/m0_37885651/article/details/79915160）

- currency(货币)
- date(日期)
- filter(子串匹配)
- json(格式化json对象)
- limitTo(限制个数)
- lowercase(小写)
- uppercase(大写)
- number(数字)
- orderBy(排序)

8.angular自定义过滤器（https://segmentfault.com/a/1190000008646187）

	代码如下：

	// file_type_data.pipe.ts
	import {Pipe, PipeTransform} from '@angular/core';
	// 管道名称
	@Pipe({name: 'file_type'})
	export class FileTypePipe implements PipeTransform {
	    public fileType = [{
	        type:'1',
	        typeName:'招标文件'
	      },{
	        type:'2',
	        typeName:'投标-技术标'
	      },{
	        type:'3',
	        typeName:'投标-商务标'
	      },{
	        type:'4',
	        typeName:'澄清'
	    }]
	  transform(type: any): string {
	    let fileName = '';
	    this.fileType.forEach((item)=>{
	        if (type == item.type){
	            fileName = item.typeName
	        }
	    })
	    return fileName;
	  }
	}

	//app.pipe.module.ts
	import {NgModule} from '@angular/core';
	import {FileTypePipe} from './utils/pipe/file_type_data.pipe';
	const pipe =  [
	  FileTypePipe
	];

	@NgModule({
	  imports: [

	  ],
	  declarations: [
	    ...pipe
	  ],
	  exports: [
	    ...pipe
	  ]
	})
	export class AppPipeModule {
	}

	// file.html
	<td>{{this.fileType | file_type}}</td>
9:ng-zrro 中checkbox不让选中

	[nzDisabled] ="bean.status == 4"
10.angular中路由跳转？（https://www.jb51.net/article/115848.html）

	// angular 路由跳转
	this.router.navigate(['/app/report/file_download_list'],{ queryParams: { relationId: bean.id } });
	// 获得？后面的参数
	this.route.queryParams.subscribe(params=> {
      this.fromData.relationId = params.relationId;
    })
	// 获得子路由的参数
	this.route.params.subscribe((params: any) => {
     console.log(params)
    });
11：angular获得当前地址的url

	import { PlatformLocation } from '@angular/common';
	constructor(private location: PlatformLocation) {
	}
	for (const i in this.location) {
	  if (i === 'location') {
	    this.locationUrl = this.location[i].href;
	    break;
	  }
	}
12:angular路由详解（https://www.jianshu.com/p/096929a2f9a3）

13:Angular5 高级教程--基于 RxJS Subject的组件间通信(https://blog.csdn.net/changerjjlee/article/details/78675290)

14:阻止事件冒泡（https://www.cnblogs.com/xuepei/p/7792556.html）；

15：常用方法（https://blog.csdn.net/qq_30101131/article/details/77169827）

16:angualr6.0怎么修改启动的默认端口号？（https://blog.csdn.net/cuiji4724/article/details/81215659）

	在node_modules中node_modules\@angular-devkit\build-angular\src\dev-server\schema.json中
	"port": {
      "type": "number",
      "description": "Port to listen on.",
      "default": 4200 // 将其修改为你想要的端口号即可
    },

17：angular5.0升级到angular6.0方法？

	重新搭建一个项目，将依赖都下全，然后将项目拷贝过去；

18：angular6.0升级到angular7？（http://www.talkingdotnet.com/upgrade-angular-6-app-angular-7-visual-studio-2017/）

1.针对目前的项目：现将typescript升级到“3.1.6”的版本；

	npm install typescript@3.1.6;

2.升级angular的版本

	ng update @angular/cli @angular/core


19:handsontable自定义渲染（https://blog.csdn.net/Juno1212/article/details/80098148）