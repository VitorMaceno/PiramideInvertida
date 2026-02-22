```js
const sleep = ms => new Promise(r => setTimeout(r, ms));
const im = n => n < 9 ? 0 : n < 99 ? 1 : n < 999 ? 2 : 3;
const mountString = (kkey, ind, w, spa) => {
    let spC = ' '.repeat(ind);
    let c = spC+[...Array(((w*2)-1)-(spC.length*2)).keys()].map((e,i) => (e+1) % 2 === 0?spa?'_':' ':'_').join('');
    return kkey+(c.slice(im(ind)));
}
const mount = async(ws = 5, spa = false) => {
    let nws = ws+1
    console.clear();
    for (let index = 0; index < nws; index++) {
        await sleep(10);
        index+1==nws ? await sleep(2000) : console.log(mountString(`${index+1}: `, index, ws, spa))
    }
    console.log('\n')
}
mount(5, true)
```
