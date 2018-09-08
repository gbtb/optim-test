use `npm run build-all` to build 3 variants of .js: 

* with --debug: index-debug.js,
* without --debug & without --optimize: index.js
* with --optimize: index-optim.js

index-debug.js is 9654 LOC,  
index.js  is 5143 LOC,  
index-optim.js is 5137 LOC.

Running `diff src/index.js src/index-optim.js` I see some record name mangling has been applied in second case, but also I found a lot of unused funcs and unremoved commented code in index-optim.js .

So, I dont understand, what is actually going on and how does --optimize works?

I also added src/index-optim-manual.js. I took index-optim.js, and removed F9 along with 2 funcs that used it -- _Json_map8 and _VirtualDom_lazy which are not used by themselves. I opened index.html with reactor and its still working. There are a lot more unused funcs in index-optim.js - from _List_map3 to _List_sortWith, some commented out code with /**_UNUSED/.

