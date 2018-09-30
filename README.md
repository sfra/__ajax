# __ajax

Simple ajax library. It do not require any additional dependencies. Two types of the library is provided:
    - regular js function
    - [require.js](https://requirejs.org/) module
    


### Installation
#### The first version (usual javaScript file)
Just put 
```html
<script type="text/javascript src="__ajax.js"></script>
```
in your head section or at the bottom of your html file.
#### The second one (Require.js module) 

Complete your main.js file
```javascript
requirejs.config({
    ...
    paths: {
    ...
        __ajax: ['classes/__ajax.require.module'] // path to the file
    ...
    }
    ...
});
```
Details can be found on [require.js](https://requirejs.org/).
### Application

An application of the library looks as follows:
```javascript
    let ajax=new __ajax('[someUrl]',{method: '[some method]'});
    ajax.setParameters([object of parameters]);
    ajax.get().then((data)=>{
        [do something with data]
    },(err)=>{})
```
For example:
```javascript
    let creditCountsNr=[];
    let ajax=new __ajax('mywebpage.php',{method: 'post'});
    ajax.setParameters({name: 'John',surname: 'Malkovich'});
    ajax.get().then((data)=>{
        creditCountsNr.push(data);
    },(err)=>{})
```
### API of __ajax

```javascript
    ajax.setParameters([obj])
```
where ```[obj]``` is js object consisting of parameters (post or get)
sending with query.

```javascript
    ajax.addParameters([obj])
```
adds (with overwriting) parameters to the existing object.

```javascript
    [obj] ajax.getParameters()
```
returns the current parameters of __ajax object.

```javascript
    ajax.setMethod([string])
```
returns the current parameters of __ajax object.

```javascript
    [obj] ajax.getParameters()
```
returns the current parameters of __ajax object.


```javascript
    [Promise] ajax.get()
```
Returns the promise of the query.
```javascript
    [Promise].then([function],[function])
```
handles the the resolving and the rejection of promise.