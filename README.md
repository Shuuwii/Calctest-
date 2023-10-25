function calculator(string) {

  const romanNumerals = ['', 'I', 'II', 'III', 'IV', 'V', 'VI', 'VII', 'VIII', 'IX', 
  'X'];
  const romanNumeralsResult = ['', 'X', 'XX', 'XXX', 'XL', 'L', 'LX', 'LXX', 'LXXX', 
  'XC', 'C'];

  let strArr = string.split(' ');

  if (strArr.length > 3 ) {
    throw new Error('можно использовать только два операнда ');
  } else if(strArr.length < 3 ) {
    throw new Error('не аерное значение');
  } else if(isNaN(strArr[0]) !== isNaN(strArr[2])) {
    throw new Error('можно использовтаь одноаеренно либо только арабские числа , либл только римские');
  } else if(!(['+', '-', '/', '*'].includes(strArr[1]))) {
    throw new Error('не корректный оператор');
  } else if(strArr[0] > 10 || strArr[2] > 10 ) {
    throw new Error('диапозон от 1-10');
  } else if(strArr[0] < 1 || strArr[2] < 1 ) {
    throw new Error('0 нельзя');
  }

  if (romanNumerals.includes(strArr[0]) && romanNumerals.includes(strArr[2])) {     
      return romanNum(strArr, romanNumerals, romanNumeralsResult);
  } else if (typeof eval(strArr.join(' ')) === typeof Number()){
      return nums(strArr);
  }
}
function romanNum(strArr, romanNumerals, romanNumeralsResult) {

  let result = String(Math.floor(eval(`${romanNumerals.indexOf(strArr[0])} ${strArr[1]} ${romanNumerals.indexOf(strArr[2])}`)));
  if (result > 0) {
  result = result.length  === 3 ? 'C': result.length > 1?  `${romanNumeralsResult[result[0]]}${romanNumerals[result[1]]}`:  `${romanNumerals[result[0]]}`;
  return(result)} else return ''
};
function nums(strArr) {
  return String(Math.floor(eval(strArr.join(' ')))) 
};
module.exports = calculator; // Не трогайте эту строчку
