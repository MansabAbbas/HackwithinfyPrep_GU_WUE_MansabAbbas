# HackwithinfyPrep_GU_WUE_MansabAbbas

Ramu has N dishes of different types arranged in a row: A1,A2,…,AN where Ai denotes the 
type of the ith dish. He wants to choose as many dishes as possible from the given list but while 
satisfying two conditions: 
1. He can choose only one type of dish. 
2. No two chosen dishes should be adjacent to each other. 
Ramu wants to know which type of dish he should choose from, so that he can pick the maximum 
number of dishes.

public class dishes {

    public static int dishes(int arr[] , int n) {
        int max = Integer.MIN_VALUE;
        for(int i=0; i<n; i++) {
            max = Math.max(max, arr[i]);
        }
        int help[] = new int[max+1];
        int c = 0;
        for(int i=0; i<arr.length-1; i++) {
            
            if(help[arr[i]] == 0) {
                help[arr[i]]++;
            }
            if(arr[i] == arr[i+1] && c==0){
                c++;
                continue;
            } else {
                help[arr[i]]++;
                c = 0;
            }
        }
        max = 0;
        int ind = -1;
        for(int i=0; i<help.length; i++) {
            if(max<help[i]) {
                max = help[i];
                ind = i;
            }
        }
        return ind;
    }
    public static void main(String args[]) {
        int arr[] = {1,2,2,1,2 };
        int n = arr.length;
        System.out.println(dishes(arr, n));
    }
}



There are three piles of stones. The first pile contains a stones, the second pile contains b stones 
and the third pile contains c stones. You must choose one of the piles and split the stones from it to 
the other two piles; specifically, if the chosen pile initially contained s stones, you should choose an 
integer k (0≤k≤s), move k stones from the chosen pile onto one of the remaining two piles and s−k 
stones onto the other remaining pile. Determine if it is possible for the two remaining piles (in any 
order) to contain x stones and y stones respectively after performing this action. 
INPUT FORMAT : 
● The first line of the input contains a single integer T denoting the number of test cases. The 
description of T test cases follows. 
● The first and only line of each test case contains five space-separated integers  
a,b,c, x and y.


public class pile {
    public static boolean solve(int a, int b, int c, int x, int y) {
        if(a<b) {
            solve(b,a,c,x,y);
        } 
        if (a<c) {
            solve(c,b,a,x,y);
        }
        if(a+b+c < x+y) {
            return false;
        }
        for(int i=0; i<=a; i++) {
            if(b+i==x && c+(a-i)==y || c+i==x && b+(a-i)==y) {
                return true;
            }
        }
        return false;
    }
    public static void main(String args[]) {
        System.out.println(solve(6,5,2,12,1));
    }
}
