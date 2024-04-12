<template>
    <div class="flex-page">
       <div class="right">
           <div class="right-header">
               <h1>WELCOME TO Jokes</h1>
               <h1>Central</h1>
           </div>
           <div>
               <h3>Embark on a journey of random giggles😀</h3>
           </div>
           <div class="flex-jokes">
               <form action="/search" method="GET">
                   <input type="text" name="query" placeholder="Search for jokes...">
                   <!-- <button id="search-jokes" type="submit"></button> -->
               </form>
           </div>

           <div class="search-key">
               <button > any</button>
               <button > programming</button>
               <button > misc</button>
               <button > dark</button>
               <button > pun</button>
               <button > spooky</button>
               <button > christmas</button>
           </div>
       </div>


       <div class="left">
           <div class="header">
               <h1>Jokes Searched</h1>
               <h3>Here are some jokes we found for you!</h3>
           </div>
           <div class="jokes">
               <p> my wife and i have reached the difficulit decision that we do 
                   not want children. if anybody does, please just send me your 
                   contact details and we can drop them off tomorrow.
               </p>
               <p> why did the banana go see a doctor? Because it wasn't
                   peeling well
               </p>
               <p>
                   my wife divorced me so i stole her wheelchair. Guess who
                   came crawling back
               </p>
               <p>
                   if you're here for the yodeling lesson, please form an orderly
                   orderly orderly queue.
               </p>
               <p>
                   what do you call a developer who doesn't comment code?
                   a devloper.
               </p>
               <p>
                   if you're here for the yodeling lesson, please form an orderly
                   orderly orderly queue.
               </p>
               <p> why did the banana go see a doctor? Because it wasn't
                   peeling well
               </p>
           </div>
       </div>

   </div>
</template>

<style>
.right{
    height: auto;
    width: 48%;
    background: linear-gradient(to right, rgb(98, 6, 134), rgb(10, 122, 197));
    animation: gradient 5s infinite alternate; 
}
.right-header{
    text-align: center;
}

.flex-jokes{
    /* background-color: white; */
    flex-direction: column;
    display: flex;
    widows: 100%;
    padding: 20px;

}
.search-joks{
    border-radius: 10px;
    border: 5px;

}
.search-key{
    /* flex-direction: column; */
    /* display: flex; */
    padding: 10px 20px;
}
.left{
    height: auto;
    width: 48%;
    border-radius: 16px;
    background-color: white;
    
}
.flex-page{
    display: flex;
    background-color: rgb(243, 239, 239);
}
.header{
    text-align: center;
}
p{
    border: 5px;
    border-radius: 5px;
    background-color: hsl(0, 0%, 90%);
    margin-top: 10px;
    margin-left: 20px;
    margin-right: 20px;
}
button{
    padding-x:4;
    padding-y:2;
    background-color: green;
    border-radius: 999px;
}
</style>