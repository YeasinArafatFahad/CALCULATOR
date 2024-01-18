<script>
    let total = 0;
    let console = "";
    let state = null;
    function resolveState(){
        switch (state) {
            case "add":
                total += parseFloat(console);
                console = "0";
                break;
            case "substract":
                total -= parseFloat(console);
                console = "0";
                break;    
            case "multiply":
                total *= parseFloat(console);
                console = "0";
                break;
            case "divide":
                total /= parseFloat(console);
                console = "0";
                break;
            default:
                total = parseFloat(console);
                console = "0";
                break;
        }
    }
    function setOperation(operation){
        resolveState();
        state = operation;
    }
    function setValue(value) {
        if (console.toString() == '0' || state == 'equal'){
            console = "";
        }
        if (state =='equal'){
            state = null;
        }
        if (value == 'C'){
            total= 0;
            state = null;
            console = "";
            return ;
        }
        console = console + value;
    }
    function equal(){
        resolveState();
        console = total;
        state = "equal";
    }
</script>
<style>
    .calculator {
        
        position:absolute;
        top:50%;
        left:50%;
        transform: translate(-50%, -50%);
        width:300px;
        border:1px solid #eee;
        box-shadow: 2px 2px 2px #eee;
        padding: 20px;
        
    }
    .calculator input{
        
        width: 100%;
        padding:20px;
        outline:none;
        text-align:right;
        font-size:20px;
    }
    .calculator .buttons{
        padding:8px;
        display: flex;
        flex-wrap:wrap;
    }
    .calculator .buttons .operations{
        display: flex;
        justify-content: space-between;
        width:100%;
       
    }
    .calculator .buttons .operations button{
        width: 100%;
        font-size: 2.25rem; /* 36px */
        line-height: 2.5rem; /* 40px */
    }
    .calculator .buttons .numbers{
        width: 75%;
    }
    .calculator .buttons .numbers > div{
        display: flex;
        justify-content: space-between;
    }
    .calculator .buttons .numbers > div button{
        width: 32%;
        font-size: 1.875rem; /* 30px */
        line-height: 2.25rem; /* 36px */
        padding-left: 1.25rem; /* 20px */
        padding-right: 1.25rem; /* 20px */
        padding-top: 0.625rem; /* 10px */
        padding-bottom: 0.625rem; /* 10px */
        border-radius: 9999px;
        margin-inline-end: 0.5rem; /* 8px */
        margin-bottom: 0.5rem; /* 8px */
        font-weight: 500;
        --tw-ring-color: rgba(229, 231, 235, var(--tw-ring-opacity));
        box-shadow: var(--tw-ring-inset) 0 0 0 calc(4px + var(--tw-ring-offset-width)) var(--tw-ring-color);
        color: rgb(0 0 0);
        outline: 2px solid transparent;
        outline-offset: 2px;
        box-shadow: var(--tw-ring-inset) 0 0 0 calc(4px + var(--tw-ring-offset-width)) var(--tw-ring-color);
        border-color: rgb(209 213 219);
        background-color: rgb(243 244 246);
        background-color:azure ;
    }
    .calculator .equal{
        flex: 2;
    }
    .calculator .equal button{
        margin-left: 40%;
        width: 95%;
        height: 95%;
        color: black;
        font-weight: 500;
        font-size: 300%;
    }
    .calculator button{
        outline: none;
    }
</style>
<div class = "calculator bg-sky-500/100" >
    <input type="text" bind:value={console} readonly = "true"/>
    <div class = "buttons">
        <div class = "operations">
            <button  on:click={()=>{setOperation('add');}} type="button" class="text-blue-700 hover:text-white border border-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center me-2 mb-2 dark:border-blue-500 dark:text-blue-500 dark:hover:text-white dark:hover:bg-blue-500 dark:focus:ring-blue-800">
                +
            </button>
            <button on:click={()=>{setOperation('substract');}} type="button" class="text-red-700 hover:text-white border border-red-700 hover:bg-red-800 focus:ring-4 focus:outline-none focus:ring-red-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center me-2 mb-2 dark:border-red-500 dark:text-red-500 dark:hover:text-white dark:hover:bg-red-600 dark:focus:ring-red-900">
                -
            </button>
            <button  on:click={()=>{setOperation('multiply');}} type="button" class="text-yellow-400 hover:text-white border border-yellow-400 hover:bg-yellow-500 focus:ring-4 focus:outline-none focus:ring-yellow-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center me-2 mb-2 dark:border-yellow-300 dark:text-yellow-300 dark:hover:text-white dark:hover:bg-yellow-400 dark:focus:ring-yellow-900">
                *
            </button>
            <button on:click={()=>{setOperation ('divide');}} type="button" class="text-purple-700 hover:text-white border border-purple-700 hover:bg-purple-800 focus:ring-4 focus:outline-none focus:ring-purple-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center me-2 mb-2 dark:border-purple-400 dark:text-purple-400 dark:hover:text-white dark:hover:bg-purple-500 dark:focus:ring-purple-900">
                /
            </button>

        </div>
        <div class = "numbers">
            <div>
                <button on:click={()=>{setValue(7);}} >
                    7
                </button>
                <button  on:click={()=>{setValue(8);}} >
                    8
                </button>
                <button  on:click={()=>{setValue(9);}} >
                    9
                </button>
            </div>
            <div>
                <button  on:click={()=>{setValue(4);}} >
                    4
                </button>
                <button  on:click={()=>{setValue(5);}} >
                    5
                </button>
                <button  on:click={()=>{setValue(6);}} >
                    6
                </button>
            </div>
            <div>
                <button on:click={()=>{setValue(1);}} >
                    1
                </button>
                <button on:click={()=>{setValue(2);}} >
                    2
                </button>
                <button on:click={()=>{setValue(3);}} >
                    3
                </button>
            </div>
            <div>
                <button on:click={()=>{setValue(0);}} >
                    0
                </button>
                <button on:click={()=>{setValue(' . ');}} >
                    .
                </button>
                <button on:click={()=>{setValue('C');}} >
                    C
                </button>
                
            </div>
        </div>
        <div class = "equal">
            <button on:click={equal} class="text-green-700 hover:text-white border border-green-700 hover:bg-green-800  focus:outline-none focus:ring-green-300  dark:border-green-500 dark:text-green-500 dark:hover:text-white dark:hover:bg-green-600 dark:focus:ring-green-800">
                =
            </button>
        </div>
    </div>
</div>