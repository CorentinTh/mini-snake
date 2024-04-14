# Snake, in the browser, in only 402 bytes

This is a simple snake game in code golf, written in pure HTML and JavaScript. It's only 404 bytes long, and it's playable in the browser.

- Move the snake with the arrow keys
- Eat the apples to grow
- Don't hit yourself -> it reset the length
- The snake can go through the walls
- Use any other key to "pause" the game

## Demo


## Code
Available in the [index.html](./index.html) file.

```html
<canvas id=c><script>d=c.getContext`2d`,x=a=b=k=[0,1],t=[],l=5,w=20,s=c.width=c.height=w*w,R=t=>Math.random()*w|0,E=t=>t+t==x+x,F=t=>d.fillStyle=t,S=t=>d.fillRect(t[0]*w,t[1]*w,w,w),onkeydown=t=>k=[[-1,0],[0,-1],[1,0],b][t.which-37],setInterval(e=>{x=b.map(t=>(x[t]+k[t]+w)%w),F`tan`,d.fillRect(0,0,s,s),F`red`,t.map(S),t.some(E)&&(l=5),t.push(x),t=t.slice(-l),E(a)&&(a=b.map(R),l++),S(a)},90)</script>
```

## Readable version
Auto formatted + added comments

```html
<canvas id="c">
<script>
  // Get the canvas element and its context
  d = c.getContext`2d`;

  // x the position of the head
  // a the position of the apple
  // b an useful array, used for directions and iterations
  // k the direction
  x = a = b = k = [0, 1];

  // t the tail
  t = [];

  // l the length of the tail
  l = 5;

  // w the width of a tile
  w = 20;

  // s the size of the canvas
  s = c.width = c.height = w * w;

  // Get a random number, cannot use new Date&w because of setInterval, it's recomputed at the same time
  R = _ => Math.random() * w | 0;
  
  // E the equality function, check if the provided coordinates are the same as the head (using array stringification)
  E = a => a + a == x + x;

  // F the fillStyle function to set the colors
  F = c => d.fillStyle = c;

  // S the fillRect function to draw a tile
  S = e => d.fillRect(e[0] * w, e[1] * w, w, w);

  // Set the direction on keydown
  onkeydown = e => k = [[-1, 0], [0, -1], [1, 0], b][e.which - 37];

  setInterval(_ => {
    // Move the head and check if it's out of bounds
    x = b.map(i => (x[i] + k[i] + w) % w);

    // Set the background color
    F`tan`;

    // Clear the canvas
    d.fillRect(0, 0, s, s);

    // Set the snake color
    F`red`;

    // Draw the tail
    t.map(S);

    // if the head is on the tail, reset the length
    t.some(E) && (l = 5);

    // Move the tail by adding the head to it and removing the last element
    t.push(x);
    t = t.slice(-l);

    // If the head is on the apple, set a new apple and increase the length
    E(a) && (a = b.map(R), l++);

    // Draw the apple
    S(a);
  }, 90);
</script>
```
## But, why?
:shrug: I don't know, I kinda like code golf.

## Contributing
Feel free to open an issue or a pull request if you have any idea to improve this project.

## Local setup
You can use `pnpm dev` to start a local vite server with HMR to ease the development.

## Credits
Coded with ❤️ by [Corentin Thomasset](//corentin.tech). 

If you want more, you can try [jugly.io](//jugly.io) a javascript code golfing platform I made.

## License
This project is under the [MIT license](LICENSE).