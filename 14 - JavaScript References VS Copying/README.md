![](https://javascript30.com/images/JS3-social-share.png)

# JavaScript30

Starter Files + Completed solutions for the JavaScript 30 Day Challenge.

Grab the course at [https://JavaScript30.com](https://JavaScript30.com)

## Object and Arrays - Reference vs Copy

1. start with strings, numbers and booleans
  
  ```javascript
  let age = 100;
  let age2 = age;
  console.log(age, age2); //100 100
  age = 200;
  console.log(age, age2); //100 200

  let name = 'Wes';
  let name2 = name;
  console.log(name, name2); //Wes Wes
  name = 'wesley';
  console.log(name, name2); //Wes wesley
  //當變數更新，age2、name2不會被更新
  ```

2. if we do the same thing as above to an array
  
  ```javascript
  const players = ['Wes', 'Sarah', 'Ryan', 'Poppy'];
  const team = players;
  console.log(players, team);
  //['Wes', 'Sarah', 'Ryan', 'Poppy']
  //['Wes', 'Sarah', 'Ryan', 'Poppy']
  team[3] = 'Lux'
  console.log(players, team);
  //['Wes', 'Sarah', 'Ryan', 'Lux']
  //['Wes', 'Sarah', 'Ryan', 'Lux']
  //players & team 皆源自於同一筆reference，所以資料會同步更新
  ```

3. Why? It's because that is an array reference, not an array copy. They both point to the same array!

4. So, how do we fix this? We take a copy instead!

  ```javascript
  // one way
  const team2 = players.slice();

  // or create a new array and concat the old one in
  const team3 = [].concat(players);

  // or use the new ES6 Spread
  const team4 = [...players];
  team4[3] = 'heeee hawww';
  console.log(players, team4);
  //['Wes', 'Sarah', 'Ryan', 'Poppy']
  //['Wes', 'Sarah', 'Ryan', 'heeee hawww']

  // or
  const team5 = Array.from(players);
  team[3] = 'cool'
  console.log(players, team5);
  //['Wes', 'Sarah', 'Ryan', 'Poppy']
  //['Wes', 'Sarah', 'Ryan', 'cool']
  ```

5. The same thing goes for objects, how do we take a copy instead? **.assign()**

  ```javascript
  const person = {
    name: 'Wes Bos',
    age: 80
  };
  const captain = person
  captain.number = 99;
  console.log(person);
  //{name: 'Wes Bos',age: 80, number: 99}

  //how do we take a copy instead?
  const cap2 = Object.assign({}, person, { number: 99, age: 12 });
  console.log(cap2);
  //{name: 'Wes Bos',age: 12, number: 99}
  console.log(person);
  //{name: 'Wes Bos',age: 80}
  ```

6. Things to note - this is only 1 level deep - both for Arrays and Objects. lodash has a cloneDeep method, but you should think twice before using it.

  ```javascript
  const wes = {
    name: 'Wes',
    age: 100,
    social: {
      twitter: '@wesbos',
      facebook: 'wesbos.developer'
    }
  };

  //1 level deep clone
  const dev = Object.assign({}, wes);
  dev.social.twitter = '@coolman'
  console.log(dev.social);
  //{twitter: '@coolman',facebook: 'wesbos.developer'}
  console.log(wes.social);
  //{twitter: '@coolman',facebook: 'wesbos.developer'}

  //clone deep
  const dev2 = JSON.parse(JSON.stringify(wes));
  dev2.social.twitter = '@coolman'
  console.log(dev.social);
  //{twitter: '@coolman',facebook: 'wesbos.developer'}
  console.log(wes.social);
  //{twitter: '@wesbos',facebook: 'wesbos.developer'}
  ```

7. further reading
  - (How to deep clone a JavaScript object)[https://flaviocopes.com/how-to-clone-javascript-object/]
  - (關於 JS 中的淺拷貝和深拷貝)[https://larry850806.github.io/2016/09/20/shallow-vs-deep-copy/]