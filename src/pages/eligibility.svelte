<script>
    import { url } from '@roxi/routify'

    let annualIncome = 0;
    let creditScore = 0;
    let employmentStatus = "";
    let eligible = false;
  
    function checkEligibility() {
      if (annualIncome >= 50000 && creditScore >= 700 && employmentStatus === "Full-time") {
        eligible = true;
      } else {
        eligible = false;
      }
    }
  </script>
  
<body>
    <main>
        
        <div class="cards">
          <a href={$url('../')}> <h3>Home</h3> </a>
          <h2>Credit Card Eligibility</h2>
          <form on:submit|preventDefault={checkEligibility}>
              <label  for="annualIncome">Annual Income:</label>
              <input type="number" class="u-full-width" id="annualIncome" bind:value={annualIncome} />
            
              <div class="credit">
                  <label for="creditScore">Credit Score:</label>
              <input type="number" id="creditScore" class="credit-input" bind:value={creditScore} />
              </div>
            
              <div class="options"><label for="employmentStatus">Employment Status:</label>
                  <select class="option-width" id="employmentStatus" bind:value={employmentStatus}>
                    <option value="Full-time">Full-time</option>
                    <option value="Part-time">Part-time</option>
                    <option value="Self-employed">Self-employed</option>
                  </select></div>
            
              <button type="submit">Check Eligibility</button>
            </form>
      
            {#if eligible}
            <p>You are eligible for a credit card.</p>
          {:else}
            <p>You are not eligible for a credit card.</p>
          {/if}
        </div>
    </main>
</body>
  



  <style>
    h3{
    width: 100px;
    height: 25px;
    color: white;
    background-color: rgb(10, 10, 10);
    text-align: center;
    border-radius: 10px;
    margin-left: 170px;
  }
    .cards{
        width: 450px;
        background-color: rgb(162, 167, 198);
        padding: 20px;
        margin: 50px auto;
        border-radius: 15px;
    }

    h2{
        margin-left: 110px;
    }

    p{
        width: 420px;
        background-color: rgb(59, 52, 132);
        border-radius: 10px;
        text-align: center;
        margin-left: 15px;
        height: 30px;
        padding-top: 7px;
        color: white;
        box-shadow: 1px 1px 4px black;
        border: 1px solid black;
    }

    .u-full-width{
    margin-top: 5px;
    width: 442px;
    height: 35px;
    border-radius: 10px;
  }

  .credit{
    display: flex;
    margin-top: 15px;
  }

  .credit-input{
    margin-left: 162px;
    border-radius: 7px;
  }

  .option-width{
    width: 210px;
    text-align: center;
   
    margin-left: 100px;
    border-radius: 7px;
  }

  button{
    width: 400px;
    margin-left: 25px;
    margin-top: 20px;
    text-align: center;
    border-radius: 10px;
    background-color: black;
    color: white;
  }

  .options{
    display: flex;
    margin-top: 15px;
  }
  label{
    font-size: 15px;
    font-weight: 600;
    margin-top: 7px;
  }

  @media only screen and (max-width: 600px){
      body{
        background-color: white;
      }
    }
  </style>