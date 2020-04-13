<template>
  <div class='app'>
    <h3 class="app-header"> Covid-19 Estimator</h3>
    <form onSubmit={this.handleSubmit} class='container' autoComplete='off'>
      <div class="main">
        <input class='input' v-model.number='population' aria-label='Population' placeholder='Population' :data-population="population"/>
        <input class='input' v-model.number='reportedCases' aria-label='Reported Cases' placeholder='Reported Cases' :data-reported-cases="reportedCases" />
        <input class='input' v-model.number='totalHospitalBeds' aria-label='Total Hospital Beds' placeholder='Total Hospital Beds' :data-total-hospital-beds="totalHospitalBeds" />
        <input class='input' v-model.number='timeToElapse' aria-label='Time Period' placeholder='Time Period' :data-time-to-elapse="timeToElapse" />
        <select class='input' v-model='periodType' aria-label='Period Type' :data-period-type="periodType">
          <option value='days' aria-label="Days">Days</option>
          <option value='weeks' aria-label="Weeks">Weeks</option>
          <option value='months' aria-label="Months">Months</option>
        </select>
      </div>
      <input type="submit" value="Submit" class='submit' @click.prevent="" data-go-estimate aria-label="Submit"/>
    </form>
  </div>
</template>

<script>

export default {
  name: 'App',
  data()  {
    return ({
      population: '',
      reportedCases: '',
      totalHospitalBeds: '',
      timeToElapse: '',
      periodType: 'days',
    });
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Roboto&display=swap');

  html, body{
    margin: 0;
    padding: 0;
  }
  .app {
    text-align: center;
    font-family: Roboto, "Segoe UI", serif;
    background-color: #282c34;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    font-size: calc(10px + 2vmin);
    color: white;
  }

  .app-header {
    padding: 1em;
    color: rgba(242, 68, 95, 0.78);
  }

  .main{
    flex: 1;
    display: flex;
    flex-direction: row;
    align-items: center;
    padding: 1em;
  }
  .container{
    flex: 1;
    flex-direction: row;
    align-items: center;
  }
  .input{
    flex: 1;
    margin: 0.3em;
    padding: 0.7em;
    background-color: rgba(40, 44, 52, 0.52);
    border: 0.2em solid rgba(165, 47, 65, 0.49);
    color: whitesmoke;
    border-radius: 0.2em;
    transition: all 250ms ease;
  }
  .input::placeholder{
    color: rgba(201, 201, 201, 0.87);
    transition: all 250ms ease;
  }
  .input:hover, .input:active, .input:visited{
    border: 0.2em solid rgba(202, 58, 80, 0.64);
    color: white;
  }
  .input:hover::placeholder, .input:active::placeholder, .input:visited::placeholder{
    color: rgba(238, 238, 238, 0.87);
  }
  .submit{
    flex: 1;
    margin: 3em;
    padding: 0.7em;
    text-transform: uppercase;
    width: calc(100vw / 4);
    border-radius: 0.5em;
    background-color: rgba(40, 44, 52, 0.52);
    border: 0.2em solid rgba(165, 47, 65, 0.49);
    color: rgba(201, 201, 201, 0.87);
    transition: all 250ms ease;
  }
  .submit:hover, .submit:visited, .submit:active{
    border: 0.2em solid rgba(202, 58, 80, 0.64);
    background-color: rgba(202, 58, 80, 0.04);
    color: white;
  }

  @media screen and (max-width: 768px) {
    .container{
      display: block;
    }
    .main{
      flex-direction: column;
    }
    .input{
      width: 100%;
      margin: 0.3em;
      padding: 0.7em;
    }
  }

</style>
