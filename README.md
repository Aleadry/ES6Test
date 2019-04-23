## Vue
# 数据绑定语法
数据绑定最基础的形式是文本插值：<span>Message: {{ msg }}</span>采用双大括号，
Mustache 标签会被相应数据对象的 msg 属性的值替换。每当这个属性变化时它也会更新。
<span>This will never change: {{* msg }}</span>单次插值处理，今后的数据变化就不会再引起插值更新了。
输出真的 HTML 字符串，需要用三 Mustache 标签：<div>{{{ raw_html }}}</div>
放在 Mustache 标签内的文本称为绑定表达式。
# vue表达式
 Vue.js 在数据绑定内支持全功能的 JavaScript 表达式：
 {{ number + 1 }}

{{ ok ? 'YES' : 'NO' }}

{{ message.split('').reverse().join('') }}
但是一个限制是每个绑定只能包含单个表达式：
<!-- 这是一个语句，不是一个表达式： -->
{{ var a = 1 }}

<!-- 流程控制也不可以，可改用三元表达式 -->
{{ if (ok) { return message } }}
# 过滤器
Vue.js 允许在表达式后添加可选的“过滤器 (Filter) ”，以“管道符”指示：
{{ message | capitalize }}
过滤器可以串联：
{{ message | filterA | filterB }}
过滤器也可以接受参数：
{{ message | filterA 'arg1' arg2 }}
引号的参数视为字符串，而不带引号的参数按表达式计算
# 指令
v-if 指令将根据表达式 greeting 值的真假删除/插入 <p> 元素：
<p v-if="greeting">Hello!</p>
v-on 指令，它用于监听 DOM 事件，这里参数是被监听的事件的名字：
<a v-on:click="doSomething">
有些指令可以在其名称后面带一个“参数” ，中间放一个冒号隔开：
<a v-bind:href="url"></a>
