using System.CodeDom.Compiler;
using System.Collections.Generic;
using System.Collections;
using System.ComponentModel;
using System.Diagnostics.CodeAnalysis;
using System.Globalization;
using System.IO;
using System.Linq;
using System.Reflection;
using System.Runtime.Serialization;
using System.Text.RegularExpressions;
using System.Text;
using System;

class Solution {

    // Complete the biggerIsGreater function below.
    static string biggerIsGreater(string w)
    {
            int j = 0;
            int shenaxuliI = 0;
            int shenaxuliJ = 0;
            int count = 0;
            bool div = false;
            bool factor = false;
            string sulAxali = "";
            for (int i = w.Length - 1; i >= 1; i--)
            {
                
                j = i - 1;
                while (true)
                {
                    if (w[i] - 'a' > w[j] - 'a')
                    {
                        div = true;
                        count++;
                        if (count == 1)
                        {
                            shenaxuliI = i;
                            shenaxuliJ = j;
                            if (i == 1)
                            {
                                div = true;
                            }
                            break;
                        }
                        if (j == shenaxuliJ)
                        {
                            if (i > shenaxuliI)
                            {
                                shenaxuliI = i;
                                shenaxuliJ = j;
                            }
                            break;
                        }
                        else if (j > shenaxuliJ)
                        {
                            if (i > shenaxuliJ)
                            {
                                shenaxuliI = i;
                                shenaxuliJ = j;
                            }
                            break;
                        }
                        else if(j < shenaxuliJ)
                        {
                            break;
                        }
                        if (i < shenaxuliJ)
                        {
                            div = true;
                            break;
                        }
                    }
                    else
                    {
                        j--;
                        if (i <= shenaxuliJ)
                        {
                            div = true;
                            break;
                        }
                        if (j < 0)
                        {
                            break;
                        }
                    }
                }                
            }
            string str1 = "";
            string str2 = "";
            string str3 = "";
            if (div == true)
            {
                if (shenaxuliJ == 0)
                {
                    factor = true;
                    char s = w[shenaxuliI];
                    w = w.Remove(shenaxuliI, 1);
                    char[] ch = w.ToArray();
                    Array.Sort(ch);
                    string axali = new string(ch);
                    sulAxali = sulAxali + s + axali;
                }
                else
                {
                    factor = true;
                    char s = w[shenaxuliI];
                    for (int k = 0; k < shenaxuliJ; k++)
                    {
                        str1 += w[k];
                    }
                    w = w.Remove(shenaxuliI, 1);
                    for (int l = shenaxuliJ; l < w.Length; l++)
                    {
                        str2 += w[l];
                        char[] ch = str2.ToCharArray();
                        Array.Sort(ch);
                        str3 = new string(ch);
                    }
                    sulAxali = sulAxali + str1 + s + str3;
                }
            }
            if (factor == true)
            {
                return sulAxali;
            }
            else
            {
                return "no answer";
            }
    }

    static void Main(string[] args) {
        TextWriter textWriter = new StreamWriter(@System.Environment.GetEnvironmentVariable("OUTPUT_PATH"), true);

        int T = Convert.ToInt32(Console.ReadLine());

        for (int TItr = 0; TItr < T; TItr++) {
            string w = Console.ReadLine();

            string result = biggerIsGreater(w);

            textWriter.WriteLine(result);
        }

        textWriter.Flush();
        textWriter.Close();
    }
}
