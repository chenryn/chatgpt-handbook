# Copilot

只需要写写注释，就能生成能够运行的代码？对于程序员群体来说，这绝对是一个提高生产力的超级工具，令人难以置信。实际上，早在2021年6月，微软和OpenAI联手推出了GitHub Copilot这一AI编程工具。它能够根据开发者的输入和上下文，生成高质量的代码片段和建议。这个工具看上去很好用很神奇，但我相信很多人仍然怀有一定的怀疑态度。让我们来亲身体验一下，看看效果如何。

首先我们需要访问 <https://github.com/features/copilot/> Copilot的官方网站开通copilot的使用权限。

![](/images/product/copilot_page.png)

我们需要先登陆github的账户，然后点击开始免费试用后会跳转到开通确认页面，这里会提示我们开通后拥有60天的免费体验的时间。

![](/images/product/copilot_free2.png)

虽然有免费体验的时间，但是我们还是要选择一个支付方案，因为试用期间不会真正扣费，所以我们大胆选择按月交费，每月10美元。点击获取访问Copilot功能按钮后就会进入下一步支付详情的页面，在这里我们要填上姓名、地址和国家。

![](/images/product/copilot_pay.png)

填写完成就可以进入支付方式表单页面，我们按照页面要求正确填写好信用卡信息。

![](/images/product/copilot_pay2.png)

填写完成后，我们点击保存支付详情按钮，当网站的后台服务完成信用卡可用性验证后，页面会跳转到Copilot配置代码提示匹配范围的页面，这里我们需要选择是否匹配公共代码，如果选择Allow，Copilot就会在整个Github的公共代码库中进行匹配然后给出代码建议，否则的话它只会在当前Github账户的organizations中进行匹配。因为我们希望体验Copilot的神奇，所以这里我们选择Allow

![](/images/product/copilot_sug.png)

当然，这个选项是可以更改的，我们可以到 <https://github.com/settings/copilot> 配置页面中进行更改。选择完成后，点击`保存并开始使用`，就会弹出支付成功的页面，页面上也提示我们可以去支持Copilot的IDE中安装插件了。

![](/images/product/copilot_paysuccess.png)

接下来我们在IDE中安装Copilot插件，这里我们使用的是VSCode，其它支持的IDE的安装方式大家可以在 <https://docs.github.com/zh/copilot/configuring-github-copilot/configuring-github-copilot-in-your-environment> 页面中找到，同时一些快捷键和使用技巧在官方文档中也都清晰的描述。

首先我们打开 VSCode 的扩展商店，搜索Copilot，会看到有许多相关的扩展，我们选择Github的官方扩展，注意不要选错了，然后点击安装。

![](/images/product/copilot_store.png)

安装完成后，右下角会出现处于加载状态的Copilot小图标，同时会提示我们需要先登录Github账号，才可以使用Copilot

![](/images/product/copilot_signin.png)

按照指引完成登录以后，Copilot的小图标就能正常显示了。

![](/images/product/copilot_icon.png)

接下来，就让我们体验一下Copilot的神奇之处，验证一下它生成的代码质量如何。这里要注意一点，Copilot是使用编程语言中的注释作为交互方式的，比如对于Javascript来说，输入`//`就可以激活Copilot，然后它会根据我们代码的上下文以及我们已经输入的部分注释内容，在代码库中匹配出合适的内容推荐出来，如果我们认为推荐的合适，可以按 `tab` 键应用推荐内容。然后按下回车开始进行下一行内容的提示。

### 斐波那契数列

作为一个经典的数学问题，Javascript实现起来也是有多种方式的，当我们注释中写完`Fabonacci 数列求和函数，函数名是 fabonacci`以后，一路按tab和回车，Copilot给我们生成了这样一份代码。

``` js
// Fabonacci 数列求和函数，函数名是 fabonacci
// 例如 fabonacci(10) // 55

function fabonacci(n) {
  if (n <= 1) {
    return n;
  }
  return fabonacci(n - 1) + fabonacci(n - 2);
}

console.log(fabonacci(10));

```
运行结果如下
![](/images/product/copilot_fab1.png)

当我写完第一行注释的描述后，它自动就推荐生成了第二行对于函数的进一步描述信息，而最终Copilot生成的代码也是按照这个注释中的描述实现的，可以看到结果完全没问题，代码的格式以及写法都算是很规范的。不过这个方法采用的是普通的递归方式实现，在数据量大的时候效率会降低，因此现在我们想用尾递归的方式实现这个方法，看看Copilot能不能帮我们写出正确的代码。

我们把注释信息修改为`Fabonacci 数列求和函数，用 尾递归 方式实现，函数名是 fabonacci`，还是一路tab加回车，基本没有手动输入什么代码，最后生成的代码如下：

```js
// Fabonacci 数列求和函数，用 尾递归 方式实现，函数名是 fabonacci
// 用法：fabonacci(10) // 55

function fabonacci(n, a = 1, b = 1) {
  if (n <= 1) {
    return b;
  }
  return fabonacci(n - 1, b, a + b);
}

console.log(fabonacci(10));
```

运行结果如下
![](/images/product/copilot_fab1.png)

看到结果，我们会发现，第二次果然是用尾递归实现了一个Fabonacci求和方法，但是两次运行的结果不一样，而且第二次，运行的结果和注释中的要求也不太一样，难道是代码有错误？经过我们对代码的审查，发现这个尾递归代码中，参数变量`a=1`表示数列从1开始，而刚才的普通递归形式的代码中没有对数列的开始值进行处理，默认是从0开始的，所以两次同样是计算长度为10的数列合，结果却产生了分歧。我们将注释细化一下，要求数列的第一项为0 看看结果如何：

```js
// Fabonacci 数列求和函数，用 尾递归 方式实现，函数名是 fabonacci
// 用法：fabonacci(10) // 55
// 数列要求从 0 开始

function fabonacci(n, a = 0, b = 1) {
  if (n <= 1) {
    return b;
  }
  return fabonacci(n - 1, b, a + b);
}

console.log(fabonacci(10));
```
运行结果如下
![](/images/product/copilot_fab3.png)

这回没问题了，两次运行的结果都是一致的了。

由此可见，如果我们在注释中没有非常明确的描述出必要的约束调教时，Capilot生成的代码可能会和我们的预期稍有不同。

### 贪吃蛇

刚刚我们使用Copilot解决了一个数学问题。这表明对于有标准算法思路的代码，它可以很好地推荐和补全代码。现在，我们要让Copilot帮我们制作一个小游戏，这种代码更偏向业务层面，需要更多的对代码上下文的理解。让我们看看这次Copilot的表现如何。

贪吃蛇这个小游戏相信大家都玩儿过，就是在一个n*m的区域中，我们使用键盘控制小蛇上下左右移动，吃到食物后小蛇长度加一；蛇头碰到自身或窗口边缘后，游戏失败。我们首先定义了一个Map类，用来构造游戏区域以及是否触及边界，绘制单元格等方法。

``` js
/**
 * ------------------------------------------------------------------
 * Map 类：用来构造游戏的区域范围，包括区域的行列等。
 * ------------------------------------------------------------------
 */
class Map {
  /**
   * 构造函数，初始化地图的行列等参数
   */
  constructor(col, row) {
    this.col = col || 24;
    this.row = row || 24;
    this.matrix = [];
    this.init();
  };
  /**
   * init() 方法：初始化地图
   */
  init() {
    if (this.row < 1 || this.col < 1) {
      throw new Error('Row and Column sizes must be at least 1');
    }
    this.matrix = [];
    for (let i = 0; i < this.row; i++) {
      this.matrix[i] = [];
      for (let j = 0; j < this.col; j++) {
        this.matrix[i][j] = 0;
      }
    }
  };
  /**
   * initMatrix() 方法：初始化地图的矩阵table，并添加到element元素上
   * @param：element 要添加到的元素
   */
  initMatrix(element) {
    // 基于 this.col和this.row 创建一个table，
    // 生成的table中每个cell存储到this.map的对应位置
    // 然后把table添加到element元素上
    let table = document.createElement("table");
    let tbody = document.createElement("tbody");
    for (let i = 0; i < this.col; i++) {
      let tr = document.createElement("tr");
      for (let j = 0; j < this.row; j++) {
        let td = document.createElement("td");
        this.matrix[i][j] = tr.appendChild(td);
      }
      tbody.appendChild(tr);
    }
    table.appendChild(tbody);
    element.appendChild(table);
  };
  
  /**
   * randomPoint(x, y) 方法：初始化地图的矩阵table，并添加到element元素上
   * @param：x 点的x坐标
   * @param：y 点的y坐标
   * @return：返回一个随机点
   * ------------------------------------------------------------------
   */
  randomPoint(x,y){
    let point = [];
    point[0] = Math.floor(Math.random()*x)+ 1;
    point[1] = Math.floor(Math.random()*y)+ 1;
    return point ;
  };

  /**
   * generateFood() 方法：根据地图的行列生成一个随机的食物
   * @return：食物的坐标
   * ------------------------------------------------------------------
   */
  generateFood() {
    const food = this.randomPoint(this.col, this.row);
    return food;
  };

  /**
   * drawCell(x, y, className): 根据坐标和类名，绘制一个cell
   * @param：x cell的x坐标
   * @param：y cell的y坐标
   * @param：className 要添加的类名
   */
  drawCell(x, y, className) {
    this.matrix[x][y].className = className;
  };

  /**
   * hitWall(point) 方法：判断是否撞墙
   * @param：point 点的坐标
   * @return：true or false
   */
  hitWall(point) {
    if(point instanceof Array){
      if(point[0]<0||point[0]>this.col-1||point[1]<0||point[1]>this.row-1){
        return true;
      }
    }
    return false;
  };
}
```
以及一个Snake类，用于描述小蛇的数据结构，判断是否触及小蛇身体等。

``` js
/**
 * ------------------------------------------------------------------
 * Snake 类：用来构造贪吃蛇，包括蛇的身体等。
 * ------------------------------------------------------------------
 */
class Snake {
  /**
   * 构造函数，初始化蛇的身体数组等参数
   */
  constructor() {
    this.body = [];
    this.init();
  };
  /**
   * init() 方法：初始化蛇的长度位置
   */
  init() {
    // 初始化蛇的位置
    this.body.push([1,3]);
    this.body.push([1,2]);
    this.body.push([1,1]);
  };
  /**
   * onSnake(point, includeHead = false) 方法：判断是否在蛇身上
   * @param：point 点的坐标
   * @param：includeHead 是否考虑作为脑袋的第一个cell
   * @return：true or false
   */
  onSnake(point, includeHead = false) {
    // 判断是否在蛇身上
    if (point instanceof Array) {
      for (var i = includeHead ? 0 : 1; i < this.body.length; i++) {
        if (point[0] == this.body[i][0] && point[1] == this.body[i][1]) {
          return true;
        }
      }
    }
    return false;
  }
}

```
上面两部分是我们准备的基础类，接下来就是Copilot大展身手的时候了，我们要实现一个Game类，用来实现游戏的初始化，小蛇的移动，游戏结果的判定等功能。按照Copilot的用法，我们先写注释，因为时业务逻辑，所以我们就尽量多的用注释将代码需要的业务逻辑描述清楚，看看结果如何。经过一系列的输入，tab和回车，Copilot帮我们生成了如下的代码：

```js
/**
 * ------------------------------------------------------------------
 * Game 类：这款游戏的主类，包括了游戏的初始化，蛇的移动等。
 * ------------------------------------------------------------------
 */
class Game {
  /**
   * 构造函数，初始化游戏，包括地图，蛇，食物等
   */
  constructor() {
    // 蛇的实例
    this.snake = new Snake();
    // 地图的实例
    this.map = new Map();
    // 食物的坐标
    this.food = [];
    // 游戏的定时器
    this.timer = null;
    // 游戏是否停止
    this.stop = true;
    // 用于存储当前按下的按键
    this.pressedKey = 0;
    // 用于存储当前蛇的移动方向
    this.nextX = 0;
    this.nextY = 1;
    this.init();
  };
  /**
   * init() 方法：初始化游戏类
   */
  init() {
    // 初始化游戏
    // 生成地图
    this.map.initMatrix(document.body)
    // 将蛇绘制在屏幕上
    this.drawSnake();
    // 生成食物
    this.newFood();
    // 绑定bind方法，用来监听键盘的按下事件
    window.addEventListener("keydown", this.bind.bind(this));
  };
  /**
   * newFood()：在地图上生成一个新的食物。
   * @returns 
   */
  newFood() {
    this.food = this.map.generateFood();
    // 调用snake实例的onSnake方法判断食物是否在蛇身上
    if (this.snake.onSnake(this.food, true)) {
      this.newFood();
      return false;
    }
    // 调用map实例的drawCell方法将食物绘制在屏幕上，类名为food
    this.map.drawCell(this.food[0],this.food[1], "food");
  };
  /**
   * drawSnake(): 调用 map 实例的drawCell接口将贪吃蛇绘制在屏幕上
   */
  drawSnake() {
    // 遍历snake实例的body数组，获取到每个cell的坐标，分别存储为_tempX和_tempY
    for(let i=0;i < this.snake.body.length; i++ ){
      let _tempX = this.snake.body[i][0], _tempY = this.snake.body[i][1];
      // 调用map实例的drawCell方法将_tempX和_tempY绘制在屏幕上，类名为snake
      this.map.drawCell(_tempX, _tempY, "snake");
    }
  };
  /**
   * bind(_e) 方法：用来监听键盘的按下事件 
   * @param _e 事件对象
   * @returns true or false
   */
  bind(_e) {
    // 将作为参数的事件对象赋值给e
    let e = _e;
    // 获取按下的键盘的键码
    let keycode = e ? e.keyCode : 0;
    // 判断按下的键码，如果是空格键，则暂停或继续游戏，如果是上下左右键，将keyCode赋值给pressedKey
    switch (keycode) {
      case 32:
        // 如果 this.stop 被设置成 true 了，就继续游戏，否则清除定时器，暂停游戏
        if (this.stop) {
          this.timer = setInterval(this.move, 200);
        } else {
          clearInterval(this.timer);
        }
        this.stop = !this.stop;
        break;
      // 上下左右键
      case 37:
      case 38:
      case 39:
      case 40:
        // 如果游戏不是暂停状态，将keyCode赋值给pressedKey
        if (!this.stop) {
          this.pressedKey = keycode;
        }
        break;
    }
    return false;
  };

  /**
   * start() 方法：游戏的主要逻辑
   */
  start() {
    // 游戏的主要逻辑
    // 首先定义蛇头所在的位置
    let x = this.snake.body[0][0];
    let y = this.snake.body[0][1];
    // 定义蛇尾所在的位置
    let tail = this.snake.body[this.snake.body.length - 1];
    // 定义游戏是否结束的标志
    let over = false;

    // 根据按下的按键来改变蛇的移动方向
    switch (this.pressedKey) {
      // 向左
      case 37:
        this.nextX = 0;
        this.nextY = -1;
        break;
      // 向上
      case 38:
        this.nextX = -1;
        this.nextY = 0;
        break;
      // 向右
      case 39:
        this.nextX = 0;
        this.nextY = 1;
        break;
      // 向下
      case 40:
        this.nextX = 1;
        this.nextY = 0;
        break;
    }
    // 根据蛇的移动方向来改变蛇头的位置
    x += this.nextX;
    y += this.nextY;
    // 判断是否吃到食物
    if (x === this.food[0] && y === this.food[1]) {
      // 如果吃到食物，将食物的位置添加到蛇的body数组中第一项作为新的蛇头
      this.snake.body.unshift([x, y]);
      // 生成新的食物
      this.newFood();
    } else {
      // 如果没有吃到食物，判断蛇是否撞到了自己或者撞到了墙
      // 先调用 map 实例的 hitWall 方法判断蛇头是否撞到了墙
      if (this.map.hitWall(x, y)) {
        over = true;
      } else if (this.snake.onSnake([x, y], false)) {
        // 再调用 snake 实例的 onSnake 方法判断蛇头是否撞到了自己
        over = true;
      }
      // 如果撞到墙或者自己了，设置游戏结束的标志为 true
      if (over) {
        // 清除定时器
        clearInterval(this.timer);
        // 弹出游戏结束的提示
        alert("游戏结束");
        return false;
      }
    }
  };
  /**
   * move() 贪吃蛇移动
   */
  move() {
    // 蛇移动
    // 使用定时器调用start方法，每隔200毫秒调用一次
    this.timer = setInterval(this.start.bind(this), 200);

  };
}
// 实例化一个Game对象
new Game();
```

我们将文件保存为snake.js，然后创建一个html文件用来作为这个小游戏的页面文件，代码如下：

```html
<!DOCTYPE>
<html>
<head>
  <title>贪吃蛇</title>
  <head>
    <style>
      * { margin: 0; padding: 0; border: 0px; }
      body { background-color: #37393b; }
      table { border-collapse: collapse; overflow: hidden; border: 1px solid #d0e3f2; margin: 8px auto; }
      td { display: table-cell; width: 16px; height: 16px; background: #87a4a9; border: 1px #bccfdf solid; }
      #info { width: 450px; margin: 24px auto; text-align: center; font-size: 14px; color: #fff;}
      .snake { background: #42e5d4; }
      .empty { background: #87a4a9; }
      .food { background: #f1ec5a; }
    </style>
  </head>
</head>
<body>
  <div>
    <p id="info">空格键控制开始，方向键控制小蛇的移动方向</p>
  </div>
  <script type="text/javascript" src="snake.js"></script>
</body>
</html>
```
在浏览器中加载后，我们看到游戏界面可以正常加载出来，那关键能不能运行呢？
我们按下空格键，却返现小蛇并没有移动，打开浏览器的控制台，看到有如下报错：

![](/images/product/copilot_error.png)

Copilot在实现绑定上下文指针`this`的代码时，使用了某代码片段中的bind方法，但是这个方法并不是Javascript解释器的方法，而我们也没有定义这个方法，所以出错了。知道原因了，我们就修复一下，使用Javascript标准的绑定上下文方法修改一下，而且有两处地方使用了bind，所以我们修改如下:

```js

class Game{

  /**
   * init() 方法：初始化游戏类
   */
  init() {
    // 初始化游戏
    // 生成地图
    this.map.initMatrix(document.body)
    // 将蛇绘制在屏幕上
    this.drawSnake();
    // 生成食物
    this.newFood();
    // 绑定bindKeydown方法，用来监听键盘的按下事件
    let _this = this;
    document.onkeydown = _this.bindContext(_this.bindKeydown, _this);
  };

  ...

  /**
   * bindContext(fn,context) 方法：用来继承运行上下文
   * @param fn 需要继承的方法
   * @param context 
   * @returns 继承以后的方法
   */
  bindContext(fn,context) {
			return function(){
				return fn.apply(context,arguments);
			}
  };

  ...

  /**
   * move() 贪吃蛇移动
   */
  move() {
    // 蛇移动
    // 使用定时器调用start方法，每隔200毫秒调用一次
    // 使用本类中的 bindContext 方法继承 this
    let _this = this;
    // 先清除定时器
    if (_this.timer) {
      clearInterval(_this.timer);
    }
    // 再重新设置定时器
    _this.timer = setInterval(_this.bindContext(_this.start, _this), 200);

  };
}

```

改好以后运行，发现还是有问题，会提示 move 方法中的`_this.bindContext` 不存在：

![](/images/product/copilot_error_2.png)

这就比较奇怪了，因为已经在方法中绑定了运行时的this上下文，说明有调用move的地方没有继承运行上下文指针this，去代码中找了一下，果然有一处异步调用没有传递上下文指针，因为这里其实不用延时调用，我们把这里改成直接调用就可以：

```js
  /**
   * bindKeydown(_e) 方法：用来监听键盘的按下事件 
   * @param _e 事件对象
   * @returns true or false
   */
  bindKeydown(_e) {
    // 将作为参数的事件对象赋值给e
    let e = _e;
    // 获取按下的键盘的键码
    let keycode = e ? e.keyCode : 0;
    // 判断按下的键码，如果是空格键，则暂停或继续游戏，如果是上下左右键，将keyCode赋值给pressedKey
    switch (keycode) {
      case 32:
        // 如果 this.stop 被设置成 true 了，就继续游戏，否则清除定时器，暂停游戏
        if (this.stop) {
          this.move();
        } else {
          clearInterval(this.timer);
        }
        this.stop = !this.stop;
        break;
      // 上下左右键
      case 37:
      case 38:
      case 39:
      case 40:
        // 如果游戏不是暂停状态，将keyCode赋值给pressedKey
        if (!this.stop) {
          this.pressedKey = keycode;
        }
        break;
    }
    return false;
  };
```

改好以后运行，这回我们的小蛇可以成功动起来，并且可以吃到食物啦，不过当我们完了一下以后，发现小蛇在撞墙的时候并没有提示结束游戏，反而报错了，报错如下：

![](/images/product/copilot_error_3.png)

经过检查，我们发现时调用是否碰撞到墙壁的方法时参数传递的问题，并没有按照方法的参数要求将坐标作为一个参数以数组的形式传递到方法中，于是我们进行了修改：
```js
  ...

  } else {
    // 如果没有吃到食物，判断蛇是否撞到了自己或者撞到了墙
    // 先调用 map 实例的 hitWall 方法判断蛇头是否撞到了墙
    if (this.map.hitWall([x, y])) {
    over = true;
    } else if (this.snake.onSnake([x, y], false)) {
    // 再调用 snake 实例的 onSnake 方法判断蛇头是否撞到了自己
    over = true;
    }
    // 如果撞到墙或者自己了，设置游戏结束的标志为 true
    if (over) {
  ...
```
这回，我们的小蛇可以正常吃到食物，撞墙也能正确提示游戏结束了，但是还是发现一个问题，当我们控制方向键的时候，如果按下和小蛇行进方向的反方向按键的时候，也提示游戏结束，这是不对的，我们需要修改一下，当按下和小蛇行进方向相反的按键时，对于下一个点的坐标不做任何改变，修改如下：

```js
    ...
    // 定义游戏是否结束的标志
    let over = false;

    // 根据按下的按键来改变蛇的移动方向
    switch (this.pressedKey) {
      // 向左
      case 37:
        if (this.nextY != 1) { this.nextX = 0; this.nextY = -1; }
        break;
      // 向上
      case 38:
        if (this.nextX != 1) { this.nextX = -1; this.nextY = 0; }
        break;
      // 向右
      case 39:
        if (this.nextY != -1) { this.nextX = 0; this.nextY = 1; }
        break;
      // 向下
      case 40:
        if (this.nextX != -1) { this.nextX = 1; this.nextY = 0; }
        break;
    }
    ...
```

这样，我们的小游戏就可以比较完美的运行了。

通过制作这个小游戏，我们可以看出Copilot在程序开发方面非常友好。它不仅能够生成正确的代码，还能理解开发者的意图和上下文，生成符合实际需求的代码片段。但是在某些特殊场景下，我们仍然需要对生成的代码进行调整，特别是在编写涉及敏感信息和安全问题的代码时，我们需要更加谨慎，避免泄露机密信息。此外，我们还应该遵守版权和知识产权相关规定，以确保不侵犯他人的权利。

