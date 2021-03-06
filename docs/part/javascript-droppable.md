﻿section: javascript
id: droppable
description: 将内容拖放到另一个容器
icon: icon-external-link
filter: tuofang tf
---

# 拖放

拖放插件帮助你将DOM元素从一个容器拖到另一个容器。

## 示例

<div class="example">
  <div class="row">
    <div class="col-md-3">
      <div class="panel">
        <div class="panel-heading">开始吧</div>
        <div class="panel-body" style="height: 120px; text-align: center; line-height: 80px">
          <button type="button" class="btn btn-danger btn-lg" data-toggle="droppable" data-target=".droppable-target"><i class="icon icon-move"></i> 拖动我</button>
        </div>
      </div>
    </div>
    <div class="col-md-3">
      <div class="panel droppable-target">
        <div class="panel-heading">拖动到这里。</div>
        <div class="panel-body" style="height: 120px">
          <div class="area-name">A</div>
        </div>
      </div>
    </div>
    <div class="col-md-3">
      <div class="panel droppable-target">
        <div class="panel-heading">这里。</div>
        <div class="panel-body" style="height: 120px">
          <div class="area-name">B</div>
        </div>
      </div>
    </div>
    <div class="col-md-3">
      <div class="panel droppable-target">
        <div class="panel-heading">或这里。</div>
        <div class="panel-body" style="height: 120px">
          <div class="area-name">C</div>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
.btn.drag-shadow {
  z-index: 9999;
}
#pageBody .btn {
  cursor: move;
}
#pageBody .area-name {
  font-size: 50px;
  line-height: 80px;
  text-align: center;
  color: #808080;
}
</style>

<script>
function afterPageLoad() {
    if($.fn.droppable) {
        $('#pageBody [data-toggle="droppable"]').droppable({
            start: function() {
                $('#pageBody .droppable-target').removeClass('panel-warning').removeClass('panel-success').find('.panel-heading').text('拖动到这里吗？');
            },
            drop: function(event) {
                var msg = '真棒！';
                $('#pageBody .droppable-target').removeClass('panel-success').removeClass('panel-warning');
                if(event.target) {
                    event.target.addClass('panel-success').find('.panel-heading').text('成功拖到目的地。');
                    msg += '成功拖动到区域 ' + event.target.find('.area-name').text();
                }
                $.zui.messager.show(msg);
            },
            drag: function(event) {

                $('#pageBody .droppable-target').removeClass('panel-success').removeClass('panel-warning');
                if(event.target) event.target.addClass('panel-warning');
            }
        });
    }
}
</script>

