# Router
####  使用Angular Router导航 
>路由的基础知识
* 基本用法
  * Routers ：url对应的哪个组件 以及RouterOutlet中展示的组件
  * RouterOutlet： 在HTML中标记路由呈现位置的占位符指令
  * Router： 负责在运行时执行路由对象，可以通过调研器navigate()和navigateByUrl()方法来导航到一个指定的路由
  * RouterLink：在Html中声明路由导航用的指令
    * 使用[]是一个数组这样可以加参数
  * ActivatedRoute：当前激活的路由对象，保存着这当前路由的信息，如路由地址，路由参数等
* 在路由时传递数据
  * 在查询参数中传递数据
  ```html
    <a [routerLink]="['/product']" [queryParams]="{id:1}">商品详情</a>
  ```
  * 在路由路径中传递数据
  ```typescript
  const routes: Routes =[ {path:/product,component:ProductComponent,data:[{isProd:true}]} => ActivatedRoute.data[0][isProd]]
  
  ngOnInit() {
      this.productId = this.routeInfo.snapshot.params['id'];
    }

  ```
  * 在路由配置中传递数据
* 参数
  * 参数快照 `this.productId = this.routeInfo.snapshot.params['id'];`
  * 参数订阅 `this.routeInfo.params.subscribe((params: Params) => this.productId = params["id"]);`
* 路由高级
  * 重定向路由 把一个地址重定向到另一个地址
  * 子路由：插座`<router-outlet></router-outlet> {path: 'xxx', Component:XxxComponet,Chidren:[{path: 'xxx', Component:XxxComponet}]}`的父子关系
  * 辅助路由：
  ```html
  <router-outlet name="aux"></router-outlet> 
  <a [routerLink]="['/home',{outlets:{aux:'xxx'}]">XXx</a>
  <a [routerLink]="['/product',{outlets:{aux:'yyy'}]">Yyy</a>
  <a [routerLink]="[{outlets:{primary:'home',aux:'chat'}}]">开始聊天</a>
  ```
  ```json
  {path: 'xxx', Component:XxxComponet,outlet:"aux"}
  ```
  * 路由守卫 -- 钩子
  > 只有当用户已经登录并拥有某些权限时才能进入某些路由，一个由多个表单组件组成的向导，例如**注册流程**，用户只有当前路由组建中填写了满足要求的信息才可以导航到下一个路由
  > 另外 当用户未执行保存操作而试图离开当前导航时提醒用户。 
    * CanActive: 处理导航到某个路由的情况
    * CanDeactivate: 处理从当前路由离开的情况
    * Resolve：在路由激活之前获取路由数据
      * 当异步返回时使用
  
  
This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 1.0.0.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive/pipe/service/class/module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `-prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).
Before running the tests make sure you are serving the app via `ng serve`.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).
