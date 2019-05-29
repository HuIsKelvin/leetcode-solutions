# 17.Letter Combinations of a Phone Number

## Difficulty:

Medium

## Description

link:
- [https://leetcode.com/problems/letter-combinations-of-a-phone-number/](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)

## Solutions

### Java

```java
class Solution {
    public List<String> letterCombinations(String digits) {
        List<String> arr1 = new ArrayList<>();
        List<String> arr2 = new ArrayList<>();
        if(digits == null || digits.length() == 0) { return arr1;}
        arr1.add("");
        for(int i = 0; i<digits.length(); i++) {
            String tmpStr = getCharByNum(digits.charAt(i));
            for(int j=0; j<arr1.size(); j++) {
                for(int k=0; k<tmpStr.length(); k++) {
                    String str = arr1.get(j) + tmpStr.charAt(k);
                    arr2.add(str);
                }
            }
            arr1 = arr2;
            arr2 = new ArrayList<>();
        }
        return arr1;
    }
    private String getCharByNum(char ch) {
        String result;
        switch(ch) {
            case '2':
                result = "abc";
                break;
            case '3':
                result = "def";
                break;
            case '4':
                result = "ghi";
                break;
            case '5':
                result = "jkl";
                break;
            case '6':
                result = "mno";
                break;
            case '7':
                result = "pqrs";
                break;
            case '8':
                result = "tuv";
                break;
            case '9':
                result = "wxyz";
                break;
            default:
                result = "";
        }
        return result;
    }
}
```