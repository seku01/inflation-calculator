# inflation-calculator

function inflationCalculator() {
    //console.log('WORKS');
    let inflationRate = document.querySelector('#inflationRate');
    let money = document.querySelector('#money');

  /*  console.log(typeof(inflation.value));  //string
    console.log(typeof(money.value));      //string

 whenever u take value from input its always a string
*/

  // inflationRate = parseInt(inflationRate.value);   //convert string to number
  // money = parseInt(money.value);                   //convert string to number
  
   // parseInt is used to convert to full number. 1 2 3... it wont show decimals
   // for decimal numbers we use parseFloat
 
   inflationRate = parseFloat(inflationRate.value);
   money = parseFloat(money.value);

   //console.log(typeof(inflationRate));  //check if its cinverted to number
   // console.log(typeof(money));      // numberrr, now we can count them down

   /* console.log(inflationRate);
      console.log(money);  
   */

  // let counting = inflationRate + money;

   // console.log(counting);  //it adds them, coz they are strings

   let years = document.querySelector('#years').value;  //u can select value like this also
   //console.log(years);
   years = parseFloat(years);   ///convert years from string to number also

   let worth = money + (money * (inflationRate / 100));  //formule for counting inflation (math)

   /* 2% inflation 1000 euro 10 years  
    using formula----  1000euro + (1000euro *(2%/100)) = 1000 +(1000*0,02)= 1000 + 20 = <<< 1020 >>> this number
    is inflation rate for only 1 year. and we still need to count for 10 years (thats the number we put inside input)
    means now we have to repeat this calculation 9 more time
    and for this we use condition (FOR)
    */

    for(let i = 1; i < years; i++) {
        worth += worth * (inflationRate / 100);
    }

    console.log(worth);

    /* 'i' is used for calculations, normally should put 0, coz it should start counting from zerro
    but we put one coz we already counted first years (which is 0 as comp starts counting from 0)
    basically here old number we got (1020) goes back again in our condition circle, computer does same formula again for 9 more times
    each time repeating same things until we get final result which is <<<1218.9944....>>>
    */

    worth = worth.toFixed(2);  //limit to show only 2 decimals after number

    let newElement = document.createElement('div');  //we create new element (div) where we will put our result
    newElement.className = 'new-value';   //we gave our div a class .new-value
    newElement.innerText = `Todays ${money} euro will be worth ${worth} euro in ${years} years.`; //write some text in our div

    document.querySelector('.container').appendChild(newElement);  //attach element to the html (inside our .container)
