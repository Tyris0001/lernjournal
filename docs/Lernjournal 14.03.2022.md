# Lernjournal 14.03.2022

# 14. March, 2022
### Table of contents
1. JavaScript FormData
2. JavaScript JSON
3. VueJs

### ToDo:
- [x] JavaScript FormData
- [x] JavaScript JSON
- [x] VueJS

### JavaScript FormData
So we're currently learning how to do Post requests with Javascript. The reasoning is that if you use the ```GET``` method, you are not able to transfer as much information compared to the ```POST``` method.
Here's an example code I've written:
```javascript
async function postData(url, data) {
  if (typeof(data) == "object") {
    var fDat = new FormData();
    for(var pair in data) {
      fDat.append(pair, data[pair]);
    }
    fetch(url, {
      method: 'POST',
      body: fDat
    })
      .then(response => response.json())
      .then(data => return data)
  } else {
    return "Parameter \"data\" is not of type \"object\"";
  }
}
var obj = {
   fileKey: "12345",
   fileName: "secretFile.txt",
   fileLength: "99999"
}
var jsonData = await postData("https://0x54.pw/file.php", obj)
console.log(await jsonData.info)
```
I have yet to try out the code, but I'm 80% sure it would work with some minimal tweaking. I have been coding **JavaScript/NodeJS** for a while now so the current tasks that we are meant to solve are not all that hard. I'm glad that we're going to be looking into cyber-security soon though because I've been slowly developing an interest in that line of work.
[[danger | Running the code]]
| I have decided to run the code and I'll be documenting the tweaks that are going to be neccessary for it to work.
[[success | Success!]]
| I forgot what tweaks I did but I managed to make it run after some minimal tweaks.

### JavaScript JSON
Now as above **JSON** is almost the same thing, I'm not 100% sure if they get parsed the same way but I know for a fact that I've worked a lot more with **JSON** than I have with **FormData**.
Here's a piece of code that sends data to a host about the same way as the code above:
```javascript
async function postData(url, data) {
  if (typeof(data) == "object") {
    fetch(url, {
      method: 'POST',
      body: JSON.stringify(data)
    })
      .then(response => response.json())
      .then(data => return data)
  } else {
    return "Parameter \"data\" is not of type \"object\";
  }
}
var obj = {
   fileKey: "12345",
   fileName: "secretFile.txt",
   fileLength: "99999"
}
var jsonData = await postData("https://0x54.pw/file.php", obj)
console.log(await jsonData.info)
```
As you can see it works about the same as the code above but instead of using **FormData** as a means of transferring data we're using **JSON** (**J**ava**S**cript **O**bject **N**otation). The ```obj``` variable converted to json should look somewhat like this:
```json
{"fileKey":"12345","fileName":"secretFile.txt","fileLength":"99999"}
```
This is what **JSON** generally looks like without any formatting. If I were to format it it'd look like this:
```json
{
  "fileKey":"12345",
  "fileName":"secretFile.txt",
  "fileLength":"99999"
}
```
Here's the testing:
[[danger | Running the code]]
| Code runs, returns a couple of errors which means that the fetch above needs to be tweaked a bit.
[[success | Success!]]
| Turns out my web-host was misconfigured and the fetch script needed no tweaking.

### Vue.js
So we've been split up in multiple groups to write about different **JavaScript** frameworks and our group just so happens to be assigned to VueJs.
Looking into Vue I first thought it'd be about the same as **electron.js** which is what [discord](https://www.discord.com/) and [slack](https://slack.com) use. Instead of just being a tool that allows you to build cross-platform tools by creating basic websites and being able to run them as an executable, Vue was made for the design and functionality of *"dashboard"-like* websites and/or panels.


> But why use VUE and not just Regular JS?

Because Vue is a lot easier to use that most of us would think.
