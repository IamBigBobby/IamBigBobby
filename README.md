# Denis Svetleishii
Front-end developer

## About me

Hi, my name is Denis. I'm 29 years old. I from Russia, was born in Novosibirsk.

I would like to tell a little story about me.

About one and half year ago, my wife foud out about rs scholl in twitter. And she offered me try myself in stage0. It was at the end of 2021. I faild. I was tried in stage1, but a couldn't resist.

But I didn't give up and continued to study.

When the war began, me, my wife and our cat left for Georgia. Now we live in Batumi.

I tried again studied on Stage0 at last summer, and I finished it. I was really happy. Unfortunately, I couldn't finish stag1 one agane.

But as you see, I have a goal and reach it.

About my education. I studied at the Siberian State University as an engineer of bridges and tunnels construction. But I didn't complete it. Because I at the first student practice, I was disappointed in my choice.

I used to work as an engineer in a construction laboratory. The work consisted in laboratory control of building materials. I have technical experience that always helps me. And now for almost 10 years I'm working as a swimming coach for preschoolers and children with special needs. This job gave me great inspiration (thanks to the children) to learn new things. I think that the combination of my past experience helps me to make a good products and be a good employee.

## Code examples

### Morse decoder
```
                const MORSE_TABLE = {
                  '.-':     'a',
                  '-...':   'b',
                  '-.-.':   'c',
                  '-..':    'd',
                  '.':      'e',
                  '..-.':   'f',
                  '--.':    'g',
                  '....':   'h',
                  '..':     'i',
                  '.---':   'j',
                  '-.-':    'k',
                  '.-..':   'l',
                  '--':     'm',
                  '-.':     'n',
                  '---':    'o',
                  '.--.':   'p',
                  '--.-':   'q',
                  '.-.':    'r',
                  '...':    's',
                  '-':      't',
                  '..-':    'u',
                  '...-':   'v',
                  '.--':    'w',
                  '-..-':   'x',
                  '-.--':   'y',
                  '--..':   'z',
                  '.----':  '1',
                  '..---':  '2',
                  '...--':  '3',
                  '....-':  '4',
                  '.....':  '5',
                  '-....':  '6',
                  '--...':  '7',
                  '---..':  '8',
                  '----.':  '9',
                  '-----':  '0',
              };
              
              function decode(expr) {
                  let result = '';
                  
                  const arrExpr = [];
                  for (let i = 0; i < expr.length; i+=10){
                      arrExpr.push(expr.slice(i, i + 10));
                  }
                  
                  const arrEachElement = [];
                  for (let element of arrExpr){
                      if (element == '**********'){
                          arrEachElement.push(' ');
                      }
                      else{
                          arrEachElement.push(element);
                      }
                  }
              
                  const arrEachElementMorse = [];
                  for (let element of arrEachElement){
                      if (element == ' '){
                          arrEachElementMorse.push(' ');
                      }
                      else{
                          element = element.replace(/10/gi, '.');
                          element = element.replace(/11/gi, '-');
                          element = element.replace(/00/gi, '')
                          arrEachElementMorse.push(element);
                      }
                  }
              
                  const finalStringResult = [];
                  for(let element of arrEachElementMorse){
                      for (key in MORSE_TABLE){
                          if (element == key){
                              finalStringResult.push(MORSE_TABLE[key]);
                          }
                          else if (element == ' '){
                              finalStringResult.push(' ');
                              break;
                          }
                      }
                  }
                  result = finalStringResult.join('');
                  return result;
              }
```
### Towel sort
```
                function towelSort (matrix) {
                  let result = '';
                  if(matrix === undefined || matrix.length === 0){
                    return result = [];
                  }
                  else{
                    const reverseMatrix = [];
                    matrix.forEach(function(item, index, array) {
                        if (index === 0){
                          reverseMatrix.push(item)
                        }
                        else if (index !== 2){
                          reverseMatrix.push(item.reverse())
                        }
                        else{
                          reverseMatrix.push(item)
                        }
                    })
                    const reverseMatrixString = reverseMatrix.join();
                    const arrReverseMatrixString = reverseMatrixString.split(',')
                    const arrFinal = [];
                      for(let element of arrReverseMatrixString){
                        if (element !== ','){
                          arrFinal.push(Number(element))
                        }
                      }
                    result = arrFinal;
                    return result;
                  }
                }
```

### Human readable number
```
               function toReadable (number) {
                  let result = '';
                  let stringNumber = number.toString();
                  let ones = ['zero', 'one', 'two', 'three', 'four', 'five', 'six', 'seven', 'eight', 'nine', 'ten', 'eleven', 'twelve', 'thirteen', 'fourteen', 'fifteen', 'sixteen', 'seventeen', 'eighteen', 'nineteen', 'twenty'];
              
                  let tens = ['', '', 'twenty', 'thirty', 'forty', 'fifty', 'sixty', 'seventy', 'eighty', 'ninety'];
              
                  if (number <= 20){
                      result = ones[number];
                  }
                  else if (number > 20 && number < 100 && stringNumber[1] != 0){
                      result = `${tens[stringNumber[0]]} ${ones[stringNumber[1]]}`;
                  }
                  else if (number > 20 && number < 100 && stringNumber[1] == 0){
                      result = `${tens[stringNumber[0]]}`;
                  }
                  else if (number >= 100){
                      if(stringNumber[1] == 0 && stringNumber[2] != 0){
                          result = `${ones[stringNumber[0]]} hundred ${ones[stringNumber[2]]}`;
                      }
                      else if(stringNumber[1] >= 1 && stringNumber[1] < 2){
                          result = `${ones[stringNumber[0]]} hundred ${ones[stringNumber.slice(1)]}`;
                      }
                      else if(stringNumber[1] >= 2 && stringNumber[2] != 0){
                          result = `${ones[stringNumber[0]]} hundred ${tens[stringNumber[1]]} ${ones[stringNumber[2]]}`
                      }
                      else if (stringNumber[0] >= 1 && stringNumber[1] == 0 && stringNumber[2] == 0){
                          result = `${ones[stringNumber[0]]} hundred`;
                      }
                      else if(stringNumber[1] > 0 && stringNumber[2] == 0){
                          result = `${ones[stringNumber[0]]} hundred ${tens[stringNumber[1]]}`;
                      }
                  }
                  return result;
              }
