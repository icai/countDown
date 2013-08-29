countDown
=========

 jquery countdown plugin which can customize styles



##Document##
<table class="classtable" cellspacing="0">
    <thead>
      <tr>
        <th width="14%">变量/函数</th>
        <th width="13%">默认值</th>
        <th width="14%">类型</th>
        <th width="59%">描述</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td class="code">startTime</td>
        <td class="code">new Date()</td>
        <td class="code">String,Date</td>        
        <td><p>当设置开始值的时候，结果就是时间差，请同时设置refresh为0，字符串必须符合w3c时间标准 new Date（‘str’）</p></td>
      </tr>    
      <tr>
        <td height="29" class="code">endTime</td>
        <td class="code">&nbsp;</td>
        <td class="code">String,Date</td>        
        <td><p>结束时间，字符串必须符合w3c时间标准 new Date（‘str’）</p></td>                    
      </tr>
      <tr>
        <td class="code">refresh</td>
        <td class="code">1000</td>
        <td class="code">Number</td>        
        <td>当值设置为0的时候，函数内部调用setTimeout</td>                    
      </tr>
      <tr>
        <td class="code">template</td>
        <td class="code">{h}:{m}:{s}.{x}</td>
        <td class="code">String</td>
        <td><p>{<br>
'Y'： '年', <br>
'M' : '月',<br>
'd' : '日',<br>
'h' : '时',<br>
'm' : '分',<br>
's' : '秒',<br>
'X' : '毫秒',<br>
'x' : '毫秒' // 除以100<br>
}</p></td>
      </tr>
      <tr>
        <td class="code">hasMonth</td>
        <td class="code">false</td>
        <td class="code">Boolean</td>        
        <td><p>设置出现最大时间单位为天，否则设为true</p></td>                    
      </tr>
      <tr>
        <td class="code">onRender</td>
        <td class="code">undefiend</td>
        <td class="code">Function</td>
        <td> <p>渲染时调用：</p>
          <p>if(this.setting.onRender &amp;&amp; this.setting.onRender.call(this,data) == false){<br>
            return false;<br>
        }</p></td>
      </tr>
      <tr>
        <td class="code">onEnd</td>
        <td class="code">undefiend</td>
        <td class="code">Function</td>        
        <td> <p>结束时调用：</p>
          <p>if(this.endFlag &amp;&amp; this.setting.onEnd &amp;&amp; this.setting.onEnd.call(this,data) == false){<br>
            return false;<br>
        }</p></td>                    
      </tr>        
             

    </tbody>
</table>



##Demo##
      $('#timer_1').countDown({
		    endTime:"2013/9/2",
		    refresh:100,
		    template:'{d}d\' {h}:{m}:{s}.{x}',
		    onEnd:function(){
		      this.container.html('过期了');
		      return false;
		    }
      })
    

##Customize styles##
      $('#timer_1').countDown({
		    endTime:"2013/9/2",
		    refresh:100,
		    template:'<span>{d}d\'<span> {h}:{m}:{s}.{x}', // Customize your styles on here
			onRender：function(data){
				console.log(data);
				this.container.html('foo bar') // Customize your styles on here ,please 'return false';
				return false;        // in order to cancel the orginal render.
			},
		    onEnd:function(){
		      this.container.html('过期了');
		      return false;
		    }
      })
    

##Core code##


        render: function(data, tmpl) {
            if (this.endFlag && this.setting.onEnd && this.setting.onEnd.call(this, data) == false) {
                return false;
            }
            if (this.setting.onRender && this.setting.onRender.call(this, data) == false) {
                return false;
            }
            tmpl = this.compile(this.setting.template, data);
            this.container.html(tmpl);
        },



##License##

The MIT License (MIT)

Copyright (c) 2013 icai

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.



