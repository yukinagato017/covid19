<template>
  <div class="about">
    <div class="details">
      <div :style="bannerAbout" class="img"></div>
      <h1>What is Covid-19?</h1>
      <p>
        Coronavirus disease 2019 (COVID-19) is defined as illness caused by a
        novel coronavirus now called severe acute respiratory syndrome
        coronavirus 2 (SARS-CoV-2; formerly called 2019-nCoV), which was first
        identified amid an outbreak of respiratory illness cases in Wuhan City,
        Hubei Province, China. [1] It was initially reported to the WHO on
        December 31, 2019. On January 30, 2020, the WHO declared the COVID-19
        outbreak a global health emergency. [2, 3] On March 11, 2020, the WHO
        declared COVID-19 a global pandemic, its first such designation since
        declaring H1N1 influenza a pandemic in 2009. [4]
        <br />
        <br />Illness caused by SARS-CoV-2 was termed COVID-19 by the WHO, the
        acronym derived from "coronavirus disease 2019. " The name was chosen to
        avoid stigmatizing the virus's origins in terms of populations,
        geography, or animal associations
      </p>
      <h1>What are the Symptoms?</h1>
      <p>Most common symptoms:</p>
      <li>Fever</li>
      <li>Dry cough</li>
      <li>Tiredness</li>
      <p>Less common symptoms:</p>
      <li>aches and pains</li>
      <li>sore throat</li>
      <li>diarrhoea</li>
      <li>conjunctivitis</li>
      <li>Dry cough</li>
      <li>headache</li>
      <li>loss of taste or smell</li>
      <li>a rash on skin, or discolouration of fingers or toes</li>
      <p>Serious symptoms:</p>
      <li>difficulty breathing or shortness of breath</li>
      <li>chest pain or pressure</li>
      <li>loss of speech or movement</li>
      <p>
        Seek immediate medical attention if you have serious symptoms. Always
        call before visiting your doctor or health facility. <br />
        People with mild symptoms who are otherwise healthy should manage their
        symptoms at home. <br />
        On average it takes 5–6 days from when someone is infected with the
        virus for symptoms to show, however it can take up to 14 days.
      </p>
      <h1>DIAGNOSIS</h1>
      <p>
        Diagnostic testing for COVID-19 involves testing for the presence of the
        virus in specimens (“swabs”) obtained from patients. Almost all
        diagnostic testing for COVID-19 is done using PCR-based methods, which
        look for the genetic material (RNA) of the SARS-CoV-2 virus, which
        causes COVID-19. These methods can only diagnose someone with COVID-19
        if they are actively infected. Currently, these diagnostic tests for
        COVID-19 require nasopharyngeal or oropharyngeal specimens (nose or
        throat swabs). Currently, PCR testing for Covid -19 has been used for
        three key purposes – one, to diagnose suspect cases to provide early
        treatment and isolate close contacts; two, to do screening and active
        case finding of individuals at risk, such as migrant workers decanted
        from their dormitories before they return to work; and three, to do
        surveillance to monitor undetected cases in the community. <br />

        <br />The terms "serological" or "antibody" tests are generally used to
        refer to blood tests that detect antibodies to the SARS-CoV-2 virus that
        causes covid-19. Serology tests can be helpful in determining whether
        someone was infected in the past with the coronavirus, whether or not
        they ever developed symptoms of the disease. Preliminary studies done
        locally have found that the sensitivity of the test is low in the first
        2 weeks of illness. In contrast, the PCR tests currently being used to
        diagnose active cases of COVID-19 indicate the presence of viral genetic
        material during the period of active infection and do not indicate if a
        person was infected and subsequently recovered.
      </p>
      <h1>TREATMENT</h1>
      <p>
        Medical care of viral pneumonia is largely supportive using medication
        and to help relieve symptoms and address severe complications such as
        bacterial infections. There are no licensed vaccines or coronavirus
        antivirals.The World Health Organization (WHO) has begun a large, global
        trial (SOLIDARITY) on the four most promising therapies identified to
        date to treat COVID-19, including chloroquine. The primary completion
        date is March 2021 with findings expected to be reported by December
        2021.
      </p>
      <h1>Home Care & Precautions</h1>
      <li>
        As much as possible, keep away from other people and pets in your home.
      </li>
      <br />
      <li>
        Wear a cloth face covering (or face mask, if you have one) if they must
        be around other people. Cloth face coverings are for use only by people
        older than 2 years old who are not having trouble breathing. Do not
        leave a child alone while they're wearing a cloth face covering. To see
        how to put on and remove cloth face coverings and face masks, clean
        them, or make your own cloth face covering, check the CDC's guide.
      </li>
      <br />
      <li>
        Cover coughs and sneezes with a tissue, throw the tissue away, and then
        wash their hands right away. Wash with soap and water for at least 20
        seconds, or use alcohol-based hand sanitizer.
      </li>
      <br />
      <li>
        If possible, stay in a bedroom and use a bathroom separate from other
        people in the home.
      </li>
      <br />
      <li>
        Use separate dishes, glasses, cups, and eating utensils and not share
        these with other household members. After use, run them through the
        dishwasher or wash with very hot soapy water.
      </li>
      <br />
      <li>
        Use separate bedding and towels and not share these with other household
        members.
      </li>

      <h2>Sources</h2>
      <a href="https://emedicine.medscape.com/article/2500114-overview#a1"
        >https://emedicine.medscape.com/article/2500114-overview#a1</a
      ><br />
      <a
        href="https://www.who.int/emergencies/diseases/novel-coronavirus-2019/question-and-answers-hub/q-a-detail/q-a-coronaviruses#:~:text=symptoms"
        >https://www.who.int/emergencies/diseases/novel-coronavirus-2019/question-and-answers-hub/q-a-detail/q-a-coronaviruses#:~:text=symptoms</a
      >
      <br /><a href="https://www.who.int/emergencies/diseases/no"
        >https://www.rafflesmedicalgroup.com/covid-19-advisory/about-covid-19</a
      >
      <br /><a
        href="https://kidshealth.org/en/parents/coronavirus-stop-spread.html"
        >https://kidshealth.org/en/parents/coronavirus-stop-spread.html</a
      >
    </div>
    <Footer />
  </div>
</template>
<script>
import Footer from "@/components/Footer.vue";
export default {
  components: {
    Footer
  },
  data() {
    return {
      bannerAbout: {
        backgroundImage: `url(${require("@/assets/3599609.jpg")})`,
        backgroundPosition: "center",
        backgroundRepeat: "no-repeat",
        backgroundSize: "cover"
      }
    };
  }
};
</script>
>
<style lang="scss" scoped>
.about {
  margin: 0px;

  p {
    text-indent: 55px;
  }
  .details {
    margin: 0px 30px;
  }
  .img {
    height: 300px;
  }
}
a {
  text-decoration: none;
}
</style>
