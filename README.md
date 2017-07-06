# hummingbird-treeview
A tiny and fast jQuery treeview plugin


## Features

- Display hierarchical tree structures.
- Based on simple HTML lists.
- Three state logic.
- Manual and programmatical check, uncheck, collapse, expand, etc.
- Supports "multi-doubles".
- Supports disabled nodes, checked or unchecked.
- Get checked/unchecked items programmatically.
- Supports HTML5 data-* attribute to embed custom data.
- Supports Font Awesome icons.
- Search function.


## Dependencies

- jQuery v3.1.1 or newer
- font-awesome v4.7.0 or newer


## Example

![alt text](./hummingbird-treeview.png "hummingbird-treeview example")


## Getting started
### Usage

Add the following resources for the hummingbird-treeview to function correctly:

```html
	
    <!-- Required Stylesheets -->
    <link href="/path/to/font-awesome.css" rel="stylesheet">
    <link href="/path/to/hummingbird-treeview.css" rel="stylesheet">

    <!-- Required Javascript -->
    <script src="/path/to/jquery.js"></script>
    <script src="/path/to/hummingbird-treeview.js"></script>

```

Bind the hummingbird-treeview to a scrollable DOM element:

```html

     <div id="treeview_container" class="hummingbird-treeview" style="height: 230px; overflow-y: scroll;">
     <!-- treeview structure/data here -->
     <div>

```

Create treeview structure/data:	

```html

    <div id="treeview_container" class="hummingbird-treeview" style="height: 230px; overflow-y: scroll;">
	<ul id="treeview">
	    <li>
		<i class="fa fa-plus"></i>
		<label>
		    <input id="xnode-0" data-id="custom-0" type="checkbox" /> node-0
		</label>
		<ul>
		    <li>
			<i class="fa fa-plus"></i>
			<label>
			    <input  id="xnode-0-1" data-id="custom-0-1" type="checkbox" /> node-0-1
			</label>
			<ul>
			    <li>
				<label>
				    <input class="hummingbirdNoParent" id="xnode-0-1-1" data-id="custom-0-1-1" type="checkbox" /> node-0-1-1
				</label>
			    </li>
			    <li>
				<label>
				    <input class="hummingbirdNoParent" id="xnode-0-1-2" data-id="custom-0-1-2" type="checkbox" /> node-0-1-2
				</label>
			    </li>
			</ul>
		    </li>
		    <li>
			<i class="fa fa-plus"></i>
			<label>
			    <input  id="xnode-0-2" data-id="custom-0-2" type="checkbox" /> node-0-2
			</label>
			<ul>
			    <li>
				<label>
				    <input class="hummingbirdNoParent" id="xnode-0-2-1" data-id="custom-0-2-1" type="checkbox" /> node-0-2-1
				</label>
			    </li>
			    <li>
				<label>
				    <input class="hummingbirdNoParent" id="xnode-0-2-2" data-id="custom-0-2-2" type="checkbox" /> node-0-2-2
				</label>
			    </li>
			</ul>
		    </li>
		</ul>
	    </li>
	</ul>
    </div>

```

Only change the following:
### Treeview structure and node properties

- **div id**<br>
  The `<div id="treeview_container"` ... can be chosen arbitrarily, but of course must be referred to consistently.
  
- **ul id**<br>
The `<ul id="treeview"` ... can be chosen.

- **input id's and data-id's**<br>
  The input id's and data-id's
  e.g. `<input id="xnode-0" data-id="custom-0"` ... can be set. The
  data-id can be any text. It is important for the support of
  multi-double nodes. That means you can have multi-double nodes with
  similar data-id's but different id's. Thus every node can be
  addressed via the unique id. And all copies of a node including
  itself can be addressed via the common data-id.

- **input class="hummingbirdNoParent"**<br>
  Add this to every node, which is
  not a parent, i.e. which has no children or nodes below.
  
Do not change the "fa fa-plus", do this via the options (see below).

Change **font-size**, **line-height**, checkbox
**width** and **height** directly in the
hummingbird-treeview.css.

Set options, e.g.:

```javascript

$.fn.hummingbird.defaults.collapsedSymbol= "fa-arrow-circle-o-right";
$.fn.hummingbird.defaults.expandedSymbol= "fa-arrow-circle-o-down";
$.fn.hummingbird.defaults.checkDoubles= true; 
$.fn.hummingbird.defaults.checkDisabled= true;
...

```    

Initialize hummingbird-treeview:

```javascript

$("#treeview").hummingbird();

```

Congratulations, you are done, your HTML list has now treeview functionality.



## Options
As you have seen above, options can be adjusted by calling

```javascript

$.fn.hummingbird.defaults.option= value;

```

Following options are available:

- **collapsedSymbol**<br>
  String, default="fa-plus". This can be any icon
  from the <a href="http://fontawesome.io/icons/">Font Awesome</a> icons.

- **expandedSymbol**<br>
  String, default="fa-minus". This can be any icon
  from the <a href="http://fontawesome.io/icons/">Font Awesome</a> icons.

- **collapseAll**<br>
  Boolean, default=true. On initialization, all
  nodes are collapsed. Change this to false to expand the nodes on initialisation.

- **checkboxes**<br>
  String, default="enabled". Checkboxes are used per
  default. Set this to "disabled" to get a
  treeview without checkboxes.
  
- **checkDoubles**<br>
  Boolean, default=false. Set this to true to enable the functionality to account for multi-doubles.

- **checkDisabled**<br>
  Boolean, default=false. Set this to true to enable the functionality to account for disabled nodes.


## Methods
Methods are used to interact with the treeview programmatically. Following methods are available:

- **checkAll()**<br>
  Checks all nodes including full support for disabled nodes.

```javascript

$("#treeview").hummingbird("checkAll");

```

- **uncheckAll()**<br>
  Unchecks all nodes including full support for disabled nodes.

```javascript

$("#treeview").hummingbird("uncheckAll");

```

- **collapseAll()**<br>
  Collapses all nodes.

```javascript

$("#treeview").hummingbird("collapseAll");

```

- **expandAll()**<br>
  Expands all nodes.

```javascript

$("#treeview").hummingbird("expandAll");

```

- **checkNode(attr,name,{expandParents})**<br>
  Checks a node, which is identified by its
  id or data-id, which has to be defined in
  the attr parameter. The name parameter
  holds the name of the id or data-id. Set
  optionally expandParents to true, if the
  parents of this node should be expanded on
  checking. Default of expandParents is
  false.

```javascript

$("#treeview").hummingbird("checkNode",{attr:"id",name: "node-0-1-1-2",expandParents:false});

```

- **uncheckNode(attr,name,{collapseChildren})**<br>
  Unchecks a node, which is identified by its
  id or data-id, which has to be defined in
  the attr parameter. The name parameter
  holds the name of the id or data-id. Set
  optionally collapseChildren to true, if the
  children of this node should be collapsed on
  unchecking. Default of collapseChildren is
  false.

```javascript

$("#treeview").hummingbird("checkNode",{attr:"id",name: "node-0-1-1-2",collapseChildren:false});

```

- **expandNode(attr,name,{expandParents})**<br>
  Expands a node, which is identified by its
  id or data-id, which has to be defined in
  the attr parameter. The name parameter
  holds the name of the id or data-id. Set
  optionally expandParents to true, if the
  parents of this node should be
  expanded. Default of expandParents is
  false.

```javascript

$("#treeview").hummingbird("expandNode",{attr:"id",name: "node-0-1-1-2",expandParents:true});

```

- **collapseNode(attr,name,{collapseChildren})**<br>
  Collapses a node, which is identified by its
  id or data-id, which has to be defined in
  the attr parameter. The name parameter
  holds the name of the id or data-id. Set
  optionally collapseChildren to true, if the
  children of this node should be
  collapsed. Default of collapseChildren is
  false.

```javascript

$("#treeview").hummingbird("collapseNode",{attr:"id",name: "node-0-1-1-2",collapseChildren:true});

```

- **disableNode(attr,name,state)**<br>
  Disables a node, which is identified by
  its id or data-id, which has to be defined
  in the attr parameter. The name parameter
  holds the name of the id or data-id.  Set
  state to true if the node should be
  disabled and checked, set it to false if
  the node should be disabled and unchecked.

```javascript

$("#treeview").hummingbird("disableNode",{attr:"id",name: "node-0-1-1-2",state:true});

```

- **enableNode(attr,name,state)**<br>
  Enables a former disabled node, which is identified by
  its id or data-id, which has to be defined
  in the attr parameter. The name parameter
  holds the name of the id or data-id.  Set
  state to true if the node should be
  enabled and checked, set it to false if
  the node should be enabled and unchecked.

```javascript

$("#treeview").hummingbird("enableNode",{attr:"id",name: "node-0-1-1-2",state:false});

```

- **getChecked(attr,List,{OnlyFinalInstance})**<br>
  Get checked nodes. Retrieve the id or
  data-id, which is defined via the attr
  parameter. Set OnlyFinalInstance to true
  if you want to retrieve only that nodes
  identified by class="hummingbirdNoParent",
  i.e. those nodes without children, so to
  speak the last instance. Default is false,
  which means that all checked nodes are retrieved.
  Define an array, e.g. List, for the output
  of this method. Finally this List array
  can be bound to a DOM element and it is
  also straight forward to do other stuff
  with that array, e.g. retrieving the
  length of it.

```javascript

var List = [];
$("#treeview").hummingbird("getChecked",{attr:"id",list:List,OnlyFinalInstance:true});
$("#displayItems").html(List.join("&#60;br&#62;"));
var L = List.length;

```

- **getUnchecked(attr,List,{OnlyFinalInstance})**<br>
  Get unchecked nodes. Retrieve the id or
  data-id, which is defined via the attr
  parameter. Set OnlyFinalInstance to true
  if you want to retrieve only that nodes
  identified by class="hummingbirdNoParent",
  i.e. those nodes without children, so to
  speak the last instance. Default is false,
  which means that all unchecked nodes are retrieved.
  Define an array, e.g. List, for the output
  of this method. Finally this List array
  can be bound to a DOM element and it is
  also straight forward to do other stuff
  with that array, e.g. retrieving the
  length of it.

```javascript

var List = [];
$("#treeview").hummingbird("getUnchecked",{attr:"id",list:List,OnlyFinalInstance:true});
$("#displayItems").html(List.join("&#60;br&#62;"));
var L = List.length;

```









































