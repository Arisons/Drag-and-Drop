5 拖拽

demo:https://codepen.io/Arison/pen/WgNLmb

在 HTML5 中，拖放是标准的一部分，任何元素都能够拖放。

5.1 拖拽和释放

拖拽：Drag

释放：Drop

拖拽指的是鼠标点击源对象后一直移动对象不松手，一但松手即释放了

5.2 设置元素为可拖放(拖放的内容 - ondragstart 和 setData())

draggable 属性：就是标签元素要设置draggable=true，否则不会有效果 

注意：  链接和图片默认是可拖动的，不需要 draggable 属性。

    document.ondragstart = function(ev) {
        ev.dataTransfer.setData("text", ev.target.id);
    }



5.2 拖拽API的相关事件

被拖动的源对象可以触发的事件：

(1)ondragstart：源对象开始被拖动

(2)ondrag：源对象被拖动过程中(鼠标可能在移动也可能未移动)

(3)ondragend：源对象被拖动结束

  拖动源对象可以进入到上方的目标对象可以触发的事件：

(1)ondragenter：目标对象被源对象拖动着进入

(2)ondragover：目标对象被源对象拖动着悬停在上方 (拖到何处 - ondragover)

(3)ondragleave：源对象拖动着离开了目标对象

(4)ondrop：源对象拖动着在目标对象上方释放/松手

拖拽API总共就是7个函数！！

这里要注意的是，ondragover为了实现拖放 ,需要阻止默认行为用return false; 或者 e.preventDefault();

    document.ondragover= function(e){
        e.preventDefault();
        // return false;
    }

5.3 DataTransfer

在进行拖放操作时，DataTransfer 对象用来保存被拖动的数据。它可以保存一项或多项数据、一种或者多种数据类型 ;

setData()

该方法向 dataTransfer 对象中存入数据。接收两个参数，第一个表示要存入数据种类的字符串，现在支持有以下几种：

- text/plain：文本文字。
- text/html：HTML文字。
- text/xml：XML文字。
- text/uri-list：URL列表，每个URL为一行。

第二个参数为要存入的数据。例如：

    event.dataTransfer.setData('text/plain','Hello World');

getData()

该方法从 dataTransfer 对象中读取数据。参数为在 setData 中指定的数据种类。例如：

    event.dataTransfer.getData('text/plain');
