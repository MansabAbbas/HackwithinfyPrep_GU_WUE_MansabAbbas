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
