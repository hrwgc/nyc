# Precinct Summary Stop and Frisk Statistics

## Data 

### Data obtained by running the following SQL query

    select new_all.pct, new_all.year, count(new_all.pct)  FROM new_all GROUP BY new_all.pct, new_all.year ORDER by new_all.pct;

The output was the taken into a spreadsheet editor application and made into a pivot table showing the totals by precinct. 


| pct | 2003 | 2004 | 2005 | 2006 | 2007 | 2008 | 2009 | 2010 | 2011 | Total Result |
| ---|---|---|---|---|---|---|---|---|---|---|
1 | 637 | 831 | 1418 | 1967 | 1887 | 2506 | 2585 | 2446 | 3626 | 17903
5 | 644 | 960 | 2493 | 3378 | 2834 | 3132 | 2880 | 2871 | 3118 | 22310
6 | 732 | 1920 | 2210 | 2597 | 3109 | 3311 | 2325 | 3533 | 2954 | 22691
7 | 1711 | 2609 | 3055 | 4207 | 4935 | 4293 | 3825 | 3224 | 4177 | 32036
9 | 1695 | 2527 | 3641 | 4450 | 4155 | 4635 | 5196 | 5177 | 5367 | 36843
10 | 1436 | 3047 | 3865 | 3127 | 3437 | 4213 | 2760 | 2728 | 3089 | 27702
13 | 768 | 1751 | 2545 | 3307 | 4250 | 5201 | 4594 | 4047 | 5252 | 31715
14 | 3155 | 4529 | 6773 | 9883 | 9701 | 11258 | 10094 | 12125 | 10665 | 78183
17 | 328 | 442 | 730 | 1429 | 1617 | 1990 | 1611 | 1842 | 2060 | 12049
18 | 870 | 1496 | 1840 | 2918 | 2570 | 3485 | 2495 | 3153 | 3633 | 22460
19 | 988 | 1248 | 3400 | 6385 | 6898 | 5394 | 3784 | 4260 | 5250 | 37607
20 | 840 | 1909 | 2446 | 3584 | 3359 | 2838 | 3041 | 4533 | 5237 | 27787
22 | 119 | 409 | 1177 | 731 | 846 | 675 | 591 | 1246 | 1416 | 7210
23 | 2982 | 5530 | 10562 | 16652 | 15188 | 15510 | 14501 | 17281 | 17498 | 115704
24 | 1276 | 1639 | 1926 | 3714 | 4713 | 4147 | 3077 | 4005 | 4918 | 29415
25 | 2601 | 3667 | 4489 | 5350 | 7915 | 8604 | 8219 | 10696 | 9926 | 61467
26 | 1130 | 2298 | 5534 | 5302 | 4320 | 4277 | 4059 | 4582 | 4991 | 36493
28 | 1715 | 2192 | 5731 | 11920 | 6410 | 6369 | 7413 | 7657 | 8738 | 58145
30 | 1197 | 5382 | 6027 | 5055 | 7211 | 3318 | 7633 | 4836 | 7550 | 48209
32 | 1970 | 5291 | 4688 | 12838 | 9934 | 11524 | 12127 | 10725 | 12859 | 81956
33 | 2261 | 3637 | 4075 | 4469 | 4769 | 4525 | 5829 | 4358 | 7041 | 40964
34 | 1792 | 3737 | 3868 | 7282 | 6717 | 7611 | 7296 | 6800 | 11548 | 56651
40 | 4243 | 7614 | 13049 | 15481 | 12662 | 12616 | 15167 | 17262 | 17690 | 115784
41 | 1950 | 2150 | 3870 | 3698 | 3386 | 7408 | 8038 | 7838 | 11329 | 49667
42 | 1720 | 4109 | 5110 | 7390 | 7483 | 8555 | 9471 | 11683 | 12414 | 67935
43 | 2127 | 3366 | 4104 | 9784 | 8951 | 10222 | 9886 | 11507 | 17281 | 77228
44 | 1677 | 3232 | 5167 | 9208 | 7997 | 8883 | 11956 | 12898 | 16903 | 77921
45 | 1161 | 1388 | 1796 | 2551 | 2635 | 3402 | 4285 | 4907 | 5362 | 27487
46 | 2262 | 3138 | 4063 | 5199 | 6068 | 7697 | 8999 | 11927 | 13718 | 63071
47 | 2590 | 4364 | 3747 | 7140 | 6961 | 7210 | 6685 | 9689 | 10936 | 59322
48 | 1317 | 2249 | 2067 | 4867 | 3317 | 4109 | 3533 | 3643 | 5265 | 30367
49 | 1573 | 2522 | 2769 | 4184 | 4750 | 4647 | 6742 | 8677 | 8495 | 44359
50 | 1829 | 2215 | 2593 | 2851 | 1766 | 2271 | 2323 | 2659 | 2683 | 21190
52 | 1610 | 2704 | 3185 | 3471 | 5011 | 7712 | 9172 | 9729 | 13648 | 56242
60 | 2715 | 3041 | 4977 | 5457 | 4377 | 6659 | 8781 | 9235 | 9952 | 55194
61 | 1579 | 2174 | 5645 | 5970 | 4472 | 6034 | 5396 | 5439 | 6620 | 43329
62 | 585 | 1400 | 4522 | 5215 | 4161 | 4642 | 6040 | 4976 | 4385 | 35926
63 | 1713 | 2754 | 4311 | 3324 | 3267 | 2218 | 2520 | 3449 | 4585 | 28141
66 | 2230 | 2495 | 4720 | 3604 | 3236 | 3800 | 3987 | 2779 | 3827 | 30678
67 | 4413 | 7470 | 7274 | 6258 | 5261 | 6860 | 12385 | 11945 | 13093 | 74959
68 | 1033 | 1136 | 2702 | 1995 | 2671 | 3385 | 2545 | 2639 | 2890 | 20996
69 | 1427 | 2199 | 4554 | 6122 | 4601 | 6694 | 5667 | 6566 | 6117 | 43947
70 | 2571 | 4955 | 10146 | 9287 | 9957 | 10479 | 10287 | 10291 | 12304 | 80277
71 | 4447 | 3564 | 3610 | 4194 | 4299 | 4817 | 6865 | 7212 | 6014 | 45022
72 | 2325 | 2382 | 3762 | 4916 | 3625 | 3743 | 3999 | 4390 | 6977 | 36119
73 | 5974 | 15533 | 10813 | 26294 | 21760 | 22960 | 26710 | 19539 | 25167 | 174750
75 | 5099 | 27078 | 31242 | 29631 | 23538 | 27771 | 31660 | 26938 | 31100 | 234057
76 | 1173 | 2035 | 4366 | 3960 | 4060 | 5546 | 5421 | 5502 | 4659 | 36722
77 | 5706 | 9662 | 17424 | 8530 | 9099 | 8321 | 10375 | 11045 | 11405 | 91567
78 | 803 | 1564 | 2468 | 2762 | 2104 | 2213 | 2432 | 3038 | 3555 | 20939
79 | 2539 | 8309 | 12810 | 15865 | 18876 | 18609 | 20726 | 15304 | 14495 | 127533
81 | 2436 | 8578 | 4530 | 5488 | 7938 | 9687 | 9101 | 11155 | 13651 | 72564
83 | 1944 | 5023 | 5133 | 5745 | 6850 | 9296 | 9436 | 9575 | 15021 | 68023
84 | 1163 | 1751 | 2049 | 3646 | 3043 | 3509 | 4010 | 4360 | 5214 | 28745
88 | 2551 | 5221 | 4076 | 6574 | 7911 | 6280 | 7156 | 7487 | 7734 | 54990
90 | 1607 | 7646 | 6779 | 8348 | 5418 | 11249 | 10398 | 10393 | 17566 | 79404
94 | 487 | 1515 | 3632 | 2934 | 2264 | 2370 | 1546 | 1913 | 2023 | 18684
100 | 1466 | 2078 | 1798 | 2402 | 3364 | 2853 | 3020 | 3468 | 5112 | 25561
101 | 2291 | 5503 | 7881 | 7874 | 8384 | 7788 | 9159 | 10007 | 11576 | 70463
102 | 3447 | 3747 | 5908 | 4239 | 4428 | 7871 | 6694 | 8406 | 9486 | 54226
103 | 6110 | 18947 | 15234 | 19463 | 10507 | 11706 | 11157 | 16420 | 17152 | 126696
104 | 1877 | 4236 | 5063 | 7631 | 6412 | 7279 | 7984 | 7591 | 6874 | 54947
105 | 1885 | 3749 | 7830 | 10972 | 7146 | 5919 | 7953 | 9747 | 9791 | 64992
106 | 2368 | 5819 | 6742 | 5522 | 4124 | 6465 | 7812 | 8446 | 8643 | 55941
107 | 2346 | 3998 | 2490 | 6228 | 5035 | 5989 | 6267 | 6723 | 5583 | 44659
108 | 2003 | 3991 | 3509 | 5321 | 7107 | 6237 | 6920 | 6743 | 5860 | 47691
109 | 3998 | 4417 | 6187 | 6443 | 7405 | 8242 | 10174 | 10200 | 12864 | 69930
110 | 2271 | 3883 | 5398 | 7452 | 8052 | 9881 | 11652 | 14368 | 10795 | 73752
111 | 1846 | 1665 | 2035 | 4616 | 3797 | 4200 | 4942 | 4705 | 4680 | 32486
112 | 1775 | 2551 | 2361 | 2890 | 2366 | 2764 | 3232 | 3195 | 3407 | 24541
113 | 2647 | 3375 | 4515 | 4910 | 6816 | 8341 | 11045 | 9154 | 12359 | 63162
114 | 3505 | 5034 | 7169 | 9399 | 9898 | 11944 | 10944 | 10887 | 10343 | 79123
115 | 1832 | 5411 | 7227 | 9626 | 5970 | 9742 | 12923 | 14023 | 18156 | 84910
120 | 5354 | 7177 | 5533 | 9954 | 10902 | 17554 | 20798 | 18529 | 16490 | 112291
122 | 2491 | 2738 | 3372 | 6276 | 6784 | 10754 | 6301 | 6601 | 9535 | 54852
123 | 982 | 1141 | 1583 | 2783 | 3049 | 4083 | 2556 | 2358 | 2027 | 20562
