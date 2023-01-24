<script>
    import { url } from '@roxi/routify'
  
  let monthlydeposit = 1000;
  let interestRate = 1;
  let years = 1;
  let compoundingFrequency = 3;
  let maturityAmount

  $:  r = interestRate / (100 * compoundingFrequency);
  $:  t = years * 12;
  $: maturityAmount = monthlydeposit * (Math.pow((1 + r), t) - 1) / r;


</script>

<body>
  <main>
    
    <div class="container">
        <div class="loan">
          <a href={$url('../')}> <h3>Home</h3> </a>
            <h1>Recurring Deposit Calculator</h1>
            <label for="input1">Monthly Deposit</label>
            <div class="input1">
              <input type="number" bind:value={monthlydeposit} class="u-full-width" placeholder="Enter Amount">
            </div>
        </div>
        <div class="year">
          <label for="years">years</label>
          <div class="years">
            <input class="u-range-width" bind:value={years} type="range" min="1" max="10" >
            <p>{years} yrs</p>
          </div>
        </div>

        <div class="interestf">
          <label for="interest">interest Rate</label>
          <div class="interest">
            <input class="u-range-width" bind:value={interestRate} type="range" >
            <p>{interestRate.toFixed(2)}%</p>
          </div>
        </div>

        <div class="year">
          <label for="years">Compounding Frequency</label>
          <div class="years">
            <input class="u-range-width" bind:value={compoundingFrequency} type="range" min="1" max="10" >
            <p>{compoundingFrequency} times a year</p>
          </div>
        </div>


        <div class="monthly">
          <div class="h3">Maturity Amount: {maturityAmount.toFixed(2)}</div>
        </div>
    </div>
</main>

</body>
<style>
  h1{
    margin-left: 55px;
  }
  h3{
    width: 100px;
    background-color: white;
    text-align: center;
    border-radius: 10px;
    margin-left: 210px;
  }
  

  label{
    font-size: 22px;
  }

  .u-full-width{
    margin-top: 5px;
    width: 500px;
    height: 25px;
    border-radius: 10px;
  }

  .years{
    display: flex;
  }

  .interest{
    display: flex;
  }

  .year{
    margin-top: 5px;
  }

  .u-range-width{
    width: 310px;
    }

    p{
      position: relative;
      top: -30px;
      width: 130px;
      margin-left: 53px;
      border: 2px solid gray;
      border-radius: 10px;
      padding: 3px;
      text-align: center;
      background-color: white;
    }

    .h3{
      width: 490px;
      text-align: center;
      border: 1px solid gray;
      padding: 8px;
      border-radius: 10px;
      margin: 5px;
      margin-left: 0;
      background-color: rgb(255, 255, 255);
    }

    .container{
      border: 2px solid black;
      width: 550px;
      padding: 20px;
      padding-left: 35px;
      padding-bottom: 45px;
      border-radius: 15px;
      margin: 50px auto;
      background-color: rgb(195, 211, 185);
    }

    body{
      background-color: gray;
    }
    @media only screen and (max-width: 600px){
      body{
        background-color: white;
      }
    }

    
</style>
  

