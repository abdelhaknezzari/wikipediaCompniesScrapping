#Extract data of UK companies from wikipedia

    library(tidyverse)

    ## Warning: package 'tidyverse' was built under R version 4.1.3

    ## -- Attaching packages --------------------------------------- tidyverse 1.3.1 --

    ## v ggplot2 3.3.5     v purrr   0.3.4
    ## v tibble  3.1.6     v dplyr   1.0.9
    ## v tidyr   1.1.4     v stringr 1.4.0
    ## v readr   2.1.1     v forcats 0.5.1

    ## Warning: package 'dplyr' was built under R version 4.1.3

    ## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

    library(rvest)

    ## 
    ## Attaching package: 'rvest'

    ## The following object is masked from 'package:readr':
    ## 
    ##     guess_encoding

    "https://en.wikipedia.org/wiki/List_of_companies_of_the_United_Kingdom_A-J" %>% read_html() %>% html_nodes(".mw-content-ltr") %>% html_children() -> vv

convert to table

    data.frame(title = vv[[1]] %>% rvest::html_elements("ul") %>% lapply(  function(x) { x %>%  html_elements("li")  %>% lapply(  function(y) { y %>% html_elements("a")  %>% lapply(   function(z) {   z %>% html_attr("title")   }  ) %>% .[1]    }  )      } ) %>% unlist(),
               href=vv[[1]] %>% rvest::html_elements("ul") %>% lapply(  function(x) { x %>%  html_elements("li")  %>% lapply(  function(y) { y %>% html_elements("a")  %>% lapply(   function(z) {   z %>% html_attr("href")   }  ) %>% .[1]    }  )      } ) %>% unlist(),
               text2=vv[[1]] %>% rvest::html_elements("ul") %>% lapply(  function(x) { x %>%  html_elements("li")  %>% lapply(  function(y) { y %>% html_elements("a")  %>% lapply(   function(z) {   z %>% html_text2()   }  ) %>% .[1]    }  )      } ) %>% unlist(),
               text=vv[[1]] %>% rvest::html_elements("ul") %>% lapply(  function(x) { x %>%  html_elements("li")  %>% lapply(  function(y) { y %>% html_elements("a")  %>% lapply(   function(z) {   z %>% html_text()   }  ) %>% .[1]    }  )      } ) %>% unlist(),
               text3 = vv[[1]] %>% rvest::html_elements("ul") %>% lapply(  function(x) { x %>%  html_elements("li")  %>% lapply(  function(y) { y %>% html_text2()   }  )      } ) %>% unlist()  %>% unlist()) -> df

Type any R code in the chunk, for example:

    df %>% knitr::kable()

<table>
<colgroup>
<col style="width: 3%" />
<col style="width: 7%" />
<col style="width: 3%" />
<col style="width: 3%" />
<col style="width: 81%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">title</th>
<th style="text-align: left;">href</th>
<th style="text-align: left;">text2</th>
<th style="text-align: left;">text</th>
<th style="text-align: left;">text3</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">NA</td>
<td style="text-align: left;">#0–9</td>
<td style="text-align: left;">0–9</td>
<td style="text-align: left;">0–9</td>
<td style="text-align: left;">0–9</td>
</tr>
<tr class="even">
<td style="text-align: left;">NA</td>
<td style="text-align: left;">#A</td>
<td style="text-align: left;">A</td>
<td style="text-align: left;">A</td>
<td style="text-align: left;">A</td>
</tr>
<tr class="odd">
<td style="text-align: left;">NA</td>
<td style="text-align: left;">#B</td>
<td style="text-align: left;">B</td>
<td style="text-align: left;">B</td>
<td style="text-align: left;">B</td>
</tr>
<tr class="even">
<td style="text-align: left;">NA</td>
<td style="text-align: left;">#C</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">C</td>
</tr>
<tr class="odd">
<td style="text-align: left;">NA</td>
<td style="text-align: left;">#D</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">D</td>
</tr>
<tr class="even">
<td style="text-align: left;">NA</td>
<td style="text-align: left;">#E</td>
<td style="text-align: left;">E</td>
<td style="text-align: left;">E</td>
<td style="text-align: left;">E</td>
</tr>
<tr class="odd">
<td style="text-align: left;">NA</td>
<td style="text-align: left;">#F</td>
<td style="text-align: left;">F</td>
<td style="text-align: left;">F</td>
<td style="text-align: left;">F</td>
</tr>
<tr class="even">
<td style="text-align: left;">NA</td>
<td style="text-align: left;">#G</td>
<td style="text-align: left;">G</td>
<td style="text-align: left;">G</td>
<td style="text-align: left;">G</td>
</tr>
<tr class="odd">
<td style="text-align: left;">NA</td>
<td style="text-align: left;">#H</td>
<td style="text-align: left;">H</td>
<td style="text-align: left;">H</td>
<td style="text-align: left;">H</td>
</tr>
<tr class="even">
<td style="text-align: left;">NA</td>
<td style="text-align: left;">#I</td>
<td style="text-align: left;">I</td>
<td style="text-align: left;">I</td>
<td style="text-align: left;">I</td>
</tr>
<tr class="odd">
<td style="text-align: left;">NA</td>
<td style="text-align: left;">#J</td>
<td style="text-align: left;">J</td>
<td style="text-align: left;">J</td>
<td style="text-align: left;">J</td>
</tr>
<tr class="even">
<td style="text-align: left;">NA</td>
<td style="text-align: left;">#References</td>
<td style="text-align: left;">References</td>
<td style="text-align: left;">References</td>
<td style="text-align: left;">References</td>
</tr>
<tr class="odd">
<td style="text-align: left;">104 Films</td>
<td style="text-align: left;">/wiki/104_Films</td>
<td style="text-align: left;">104 Films</td>
<td style="text-align: left;">104 Films</td>
<td style="text-align: left;">104 Films — is a film production company. Established in 2004, its headquarters is in Birmingham.</td>
</tr>
<tr class="even">
<td style="text-align: left;">24seven (company)</td>
<td style="text-align: left;">/wiki/24seven_(company)</td>
<td style="text-align: left;">24seven</td>
<td style="text-align: left;">24seven</td>
<td style="text-align: left;">24seven — was an energy company (electricity supply) from 2000 to 2003. Its parent companies were London Electricity, and TXU Europe. In 2003 it became part of LE Group.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">3 Mills Studios</td>
<td style="text-align: left;">/wiki/3_Mills_Studios</td>
<td style="text-align: left;">3 Mills Studios</td>
<td style="text-align: left;">3 Mills Studios</td>
<td style="text-align: left;">3 Mills Studios — is a centre for film and TV production. It is located in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">A.G. Barr</td>
<td style="text-align: left;">/wiki/A.G._Barr</td>
<td style="text-align: left;">A.G. Barr</td>
<td style="text-align: left;">A.G. Barr</td>
<td style="text-align: left;">A.G. Barr – is a soft drinks manufacturer best known for the drink Irn-Bru. Established in 1875 by Robert Barr in Falkirk, Scotland, it is now headquartered in Cumbernauld, Scotland. Its production sites are in Cumbernauld, Forfar, and Milton Keynes. In 2019 its revenue was £279 million, with a net income of £35.8 million.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">AAH Pharmaceuticals</td>
<td style="text-align: left;">/wiki/AAH_Pharmaceuticals</td>
<td style="text-align: left;">AAH Pharmaceuticals</td>
<td style="text-align: left;">AAH Pharmaceuticals</td>
<td style="text-align: left;">AAH Pharmaceuticals — is a pharmaceuticals wholesaler, formerly anthracite producer and supplier, building materials, transport, warehousing, and environmental services. Established in 1892, its headquarters is in Coventry. It was formerly named Amalgamated Anthracite Collieries. In 1995 it was bought by Celesio AG.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Aardman Animations</td>
<td style="text-align: left;">/wiki/Aardman_Animations</td>
<td style="text-align: left;">Aardman Animations</td>
<td style="text-align: left;">Aardman Animations</td>
<td style="text-align: left;">Aardman Animations – is a film studio producing animation films and television programmes. Established in 1972, its headquarters is in Bristol.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Abbey National</td>
<td style="text-align: left;">/wiki/Abbey_National</td>
<td style="text-align: left;">Abbey National</td>
<td style="text-align: left;">Abbey National</td>
<td style="text-align: left;">Abbey National — was a financial services company (banking, and investment; it was previously a building society and estate agent), 1944–2010. Its headquarters is in London. Also known as Abbey, it was formed by the merger of the Abbey Road Building Society with the National Building Society. In 2010 it was subsumed into Santander UK.</td>
</tr>
<tr class="even">
<td style="text-align: left;">AbbottVision</td>
<td style="text-align: left;">/wiki/AbbottVision</td>
<td style="text-align: left;">AbbottVision</td>
<td style="text-align: left;">AbbottVision</td>
<td style="text-align: left;">AbbottVision — is a film and TV production company. Established in 2008, its headquarters is in Manchester.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">ABC Cinemas</td>
<td style="text-align: left;">/wiki/ABC_Cinemas</td>
<td style="text-align: left;">ABC Cinemas</td>
<td style="text-align: left;">ABC Cinemas</td>
<td style="text-align: left;">ABC Cinemas — was a cinema chain from 1927 to 2017.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Abcam</td>
<td style="text-align: left;">/wiki/Abcam</td>
<td style="text-align: left;">Abcam</td>
<td style="text-align: left;">Abcam</td>
<td style="text-align: left;">Abcam — is a biotechnology and life sciences company (research of antibodies, kits and assays for biological research). It was established in 1998.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Abcodia</td>
<td style="text-align: left;">/wiki/Abcodia</td>
<td style="text-align: left;">Abcodia</td>
<td style="text-align: left;">Abcodia</td>
<td style="text-align: left;">Abcodia — is a biotechnology company (biomarkers for cancer screening). Established in 2010, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Aberdeen Asset Management</td>
<td style="text-align: left;">/wiki/Aberdeen_Asset_Management</td>
<td style="text-align: left;">Aberdeen Asset Management</td>
<td style="text-align: left;">Aberdeen Asset Management</td>
<td style="text-align: left;">Aberdeen Asset Management — was an investment management company from 1983 to 2017. Its headquarters was in Aberdeen, Scotland. In 2017 it was merged with Standard Life to form Standard Life Aberdeen, since rebranded as Abrdn</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Abrdn</td>
<td style="text-align: left;">/wiki/Abrdn</td>
<td style="text-align: left;">Abrdn</td>
<td style="text-align: left;">Abrdn</td>
<td style="text-align: left;">Abrdn — is a financial services company (global investment, asset management, formerly banking and insurance). Established in 1825, its headquarters is in Edinburgh, Scotland. It was formerly known as the Standard Life Assurance Company. In 2017 it was merged with Aberdeen Asset Management to form Standard Life Aberdeen plc. In 2019 its revenue was £1.6 billion, with net revenue of £210 million.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Academy Films</td>
<td style="text-align: left;">/wiki/Academy_Films</td>
<td style="text-align: left;">Academy Films</td>
<td style="text-align: left;">Academy Films</td>
<td style="text-align: left;">Academy Films — is a film and TV production company. Established in 1985, its headquarters was in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Acteon Group (company)</td>
<td style="text-align: left;">/wiki/Acteon_Group_(company)</td>
<td style="text-align: left;">Acteon Group</td>
<td style="text-align: left;">Acteon Group</td>
<td style="text-align: left;">Acteon Group — is a subsea services company (mainly supplying the oil, gas, and renewable industries). Established in 2004, its headquarters is in Norwich, Norfolk. It was formed from the UWG Group.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Adam &amp; Company</td>
<td style="text-align: left;">/wiki/Adam_%26_Company</td>
<td style="text-align: left;">Adam &amp; Company</td>
<td style="text-align: left;">Adam &amp; Company</td>
<td style="text-align: left;">Adam &amp; Company — is a financial services company (private banking and investment management). Established in 1983, its headquarters is in Edinburgh, Scotland. In 2018, the retail banking assets of Royal Bank of Scotland were transferred to Adam and Company, which was renamed Royal Bank of Scotland, with Adam and Company continuing as a trading name of the Royal Bank of Scotland.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Adelphi Films</td>
<td style="text-align: left;">/wiki/Adelphi_Films</td>
<td style="text-align: left;">Adelphi Films</td>
<td style="text-align: left;">Adelphi Films</td>
<td style="text-align: left;">Adelphi Films — is a film production and distribution company. It was established in 1939.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Affinity Water</td>
<td style="text-align: left;">/wiki/Affinity_Water</td>
<td style="text-align: left;">Affinity Water</td>
<td style="text-align: left;">Affinity Water</td>
<td style="text-align: left;">Affinity Water — is a utility company (water supply). Established in 2012, its headquarters is in Hatfield, Hertfordshire. It was formed by the purchase and merger of Veolia Water Central, Veolia Water Southeast, and Veolia Water East.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">AfriMobile</td>
<td style="text-align: left;">/wiki/AfriMobile</td>
<td style="text-align: left;">AfriMobile</td>
<td style="text-align: left;">AfriMobile</td>
<td style="text-align: left;">AfriMobile — is a telecommunications company (mobile virtual network operator). It was established in 2012.</td>
</tr>
<tr class="even">
<td style="text-align: left;">African Potash</td>
<td style="text-align: left;">/wiki/African_Potash</td>
<td style="text-align: left;">African Potash</td>
<td style="text-align: left;">African Potash</td>
<td style="text-align: left;">African Potash — is mining company involved in the production and distribution of fertiliser. It was established in 2011.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Air Navigation and Engineering Company</td>
<td style="text-align: left;">/wiki/Air_Navigation_and_Engineering_Company</td>
<td style="text-align: left;">Air Navigation and Engineering Company</td>
<td style="text-align: left;">Air Navigation and Engineering Company</td>
<td style="text-align: left;">Air Navigation and Engineering Company — was an aircraft, and cyclecar manufacturer from 1919 to 1927. Its headquarters was in Addlestone, Surrey. It was formerly the Bleriot &amp; SPAD Manufacturing Company.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Vauxhall Motors</td>
<td style="text-align: left;">/wiki/Vauxhall_Motors</td>
<td style="text-align: left;">Vauxhall Motors</td>
<td style="text-align: left;">Vauxhall Motors</td>
<td style="text-align: left;">Alex Wilson &amp; Company — was an engine manufacturering company, see Vauxhall Motors.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Allen &amp; Hanburys</td>
<td style="text-align: left;">/wiki/Allen_%26_Hanburys</td>
<td style="text-align: left;">Allen &amp; Hanburys</td>
<td style="text-align: left;">Allen &amp; Hanburys</td>
<td style="text-align: left;">Allen &amp; Hanburys — was a pharmaceuticals manufacturer from 1715 to 1958. Headquartered in London, it was absorbed by Glaxo Laboratories in 1958.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Alliance &amp; Leicester</td>
<td style="text-align: left;">/wiki/Alliance_%26_Leicester</td>
<td style="text-align: left;">Alliance &amp; Leicester</td>
<td style="text-align: left;">Alliance &amp; Leicester</td>
<td style="text-align: left;">Alliance &amp; Leicester — was a financial services company (banking and insurance; it was formerly a building society) from 1985 to 2011. Its headquarters was in Narborough, Leicestershire. It was formed by the merger of the Alliance Building Society with the Leicester Building Society. In 2011 it was subsumed into Santander UK.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Allied Film Makers</td>
<td style="text-align: left;">/wiki/Allied_Film_Makers</td>
<td style="text-align: left;">Allied Film Makers</td>
<td style="text-align: left;">Allied Film Makers</td>
<td style="text-align: left;">Allied Film Makers — was a film production company. Established in 1959, it is defunct.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Allied Stars</td>
<td style="text-align: left;">/wiki/Allied_Stars</td>
<td style="text-align: left;">Allied Stars</td>
<td style="text-align: left;">Allied Stars</td>
<td style="text-align: left;">Allied Stars — was a film production company. It was established in the late 1970s.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Amersham plc</td>
<td style="text-align: left;">/wiki/Amersham_plc</td>
<td style="text-align: left;">Amersham plc</td>
<td style="text-align: left;">Amersham plc</td>
<td style="text-align: left;">Amersham plc — was a manufacturer of radiopharmaceutical products for nuclear medicine from 1946 to 2003. Its headquarters was in Amersham, Buckinghamshire. It was previously known as The Radiochemical Centre (RTC) Amersham, Amersham International, and Nycomed Amersham. In 2003 it was acquired by General Electric and incorporated into GE Healthcare.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Amicus Productions</td>
<td style="text-align: left;">/wiki/Amicus_Productions</td>
<td style="text-align: left;">Amicus Productions</td>
<td style="text-align: left;">Amicus Productions</td>
<td style="text-align: left;">Amicus Productions — was a film production company from 1962 to 1977. It was based at Shepperton Studios.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Andrew Knowles and Sons</td>
<td style="text-align: left;">/wiki/Andrew_Knowles_and_Sons</td>
<td style="text-align: left;">Andrew Knowles and Sons</td>
<td style="text-align: left;">Andrew Knowles and Sons</td>
<td style="text-align: left;">Andrew Knowles and Sons — was a coal mining company from circa 1805 to 1929. It became part of Manchester Collieries.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Anglesey Mining</td>
<td style="text-align: left;">/wiki/Anglesey_Mining</td>
<td style="text-align: left;">Anglesey Mining</td>
<td style="text-align: left;">Anglesey Mining</td>
<td style="text-align: left;">Anglesey Mining — is a mining company.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Anglian Water</td>
<td style="text-align: left;">/wiki/Anglian_Water</td>
<td style="text-align: left;">Anglian Water</td>
<td style="text-align: left;">Anglian Water</td>
<td style="text-align: left;">Anglian Water — is a utility company (water supply and sewage). Established in 1979, its headquarters is in Huntingdon, Cambridgeshire. It was preceded by Anglian Water Authority. Its parent company is Anglian Water Group.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Anglian Water Authority</td>
<td style="text-align: left;">/wiki/Anglian_Water_Authority</td>
<td style="text-align: left;">Anglian Water Authority</td>
<td style="text-align: left;">Anglian Water Authority</td>
<td style="text-align: left;">Anglian Water Authority — was a state owned utility company (water supply and sewage) from 1974 to 1979. It was succeeded by Anglian Water.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Anglian Water Group</td>
<td style="text-align: left;">/wiki/Anglian_Water_Group</td>
<td style="text-align: left;">Anglian Water Group</td>
<td style="text-align: left;">Anglian Water Group</td>
<td style="text-align: left;">Anglian Water Group — is a holding company that is parent to Anglian Water. Headquartered in Huntingdon, it is owned by Osprey Consortium.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Anglo-Amalgamated</td>
<td style="text-align: left;">/wiki/Anglo-Amalgamated</td>
<td style="text-align: left;">Anglo-Amalgamated</td>
<td style="text-align: left;">Anglo-Amalgamated</td>
<td style="text-align: left;">Anglo-Amalgamated — was a film production and distribution company from 1945 to 1971.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">EMI Films</td>
<td style="text-align: left;">/wiki/EMI_Films</td>
<td style="text-align: left;">EMI Films</td>
<td style="text-align: left;">EMI Films</td>
<td style="text-align: left;">Anglo—EMI Film Distributors Ltd — was a film production and distribution company, see EMI Films.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Anglo American plc</td>
<td style="text-align: left;">/wiki/Anglo_American_plc</td>
<td style="text-align: left;">Anglo American</td>
<td style="text-align: left;">Anglo American</td>
<td style="text-align: left;">Anglo American — is a British multinational mining company. Established in 1917, its headquarters are in London, UK and Johannesburg, South Africa. Its 2019 revenue was $29.8 billion, with net income of $4.5 billion.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Anglo Pacific Group</td>
<td style="text-align: left;">/wiki/Anglo_Pacific_Group</td>
<td style="text-align: left;">Anglo Pacific Group</td>
<td style="text-align: left;">Anglo Pacific Group</td>
<td style="text-align: left;">Anglo Pacific Group — is a mining finance company (resources royalties). Established in 1967, its headquarters is in London. It was formerly known as Diversified Bank Shares Limited.</td>
</tr>
<tr class="even">
<td style="text-align: left;">AP Films</td>
<td style="text-align: left;">/wiki/AP_Films</td>
<td style="text-align: left;">AP Films</td>
<td style="text-align: left;">AP Films</td>
<td style="text-align: left;">AP Films — (APF) was a television and film production, and publishing company from 1957 to 1977. Its headquarters was in Maidenhead, Berkshire. It later became Century 21 Productions.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Apollo Cinemas</td>
<td style="text-align: left;">/wiki/Apollo_Cinemas</td>
<td style="text-align: left;">Apollo Cinemas</td>
<td style="text-align: left;">Apollo Cinemas</td>
<td style="text-align: left;">Apollo Cinemas — was a cinema chain from 2002 to 2013.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Arash Motor Company</td>
<td style="text-align: left;">/wiki/Arash_Motor_Company</td>
<td style="text-align: left;">Arash Motor Company</td>
<td style="text-align: left;">Arash Motor Company</td>
<td style="text-align: left;">Arash Motor Company — is an automobile manufacturer. Established in 1999, its headquarters is in Newmarket, Suffolk. It was formerly named Farboud Limited.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Archers Film Productions</td>
<td style="text-align: left;">/wiki/Archers_Film_Productions</td>
<td style="text-align: left;">Archers Film Productions</td>
<td style="text-align: left;">Archers Film Productions</td>
<td style="text-align: left;">Archers Film Productions — was a film production company from 1943 to 1957.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Argos (retailer)</td>
<td style="text-align: left;">/wiki/Argos_(retailer)</td>
<td style="text-align: left;">Argos</td>
<td style="text-align: left;">Argos</td>
<td style="text-align: left;">Argos — is a catalogue retailer (shops and online). Established in 1972, its headquarters is in Milton Keynes, Buckinghamshire. Its parent company is Sainsbury’s. Its 2016 revenue was £4.1 billion and its 2016 operating income was £83.1 million.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Aria Films</td>
<td style="text-align: left;">/wiki/Aria_Films</td>
<td style="text-align: left;">Aria Films</td>
<td style="text-align: left;">Aria Films</td>
<td style="text-align: left;">Aria Films — is a film production, finance, and consultancy company. Established in 2002, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Aricom</td>
<td style="text-align: left;">/wiki/Aricom</td>
<td style="text-align: left;">Aricom</td>
<td style="text-align: left;">Aricom</td>
<td style="text-align: left;">Aricom — was a mining and metals company from 2003 to 2009/10. Its headquarters was in London. It was formerly part of Peter Hambro Mining who, as Petropavlovsk reacquired it in 2009.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Ariel Motor Company</td>
<td style="text-align: left;">/wiki/Ariel_Motor_Company</td>
<td style="text-align: left;">Ariel Motor Company</td>
<td style="text-align: left;">Ariel Motor Company</td>
<td style="text-align: left;">Ariel Motor Company — is an automobile and motor bike manufacturer. Established in 1991 its headquarters is in Crewkerne, Somerset. It was formerly named Solocrest Ltd.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Armstrong Siddeley</td>
<td style="text-align: left;">/wiki/Armstrong_Siddeley</td>
<td style="text-align: left;">Armstrong Siddeley</td>
<td style="text-align: left;">Armstrong Siddeley</td>
<td style="text-align: left;">Armstrong Siddeley — was a manufacturer of automobiles, aircraft engines and light engineering from 1919 to 1960. Headquartered in Coventry, it was established by the merger of Armstrong Whitworth with Siddeley-Deasy. There were later mergers/takeovers with Hawker Aircraft, and Bristol Aero Engines. In 1960 it became Bristol Siddeley.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Armstrong-CCM Motorcycles</td>
<td style="text-align: left;">/wiki/Armstrong-CCM_Motorcycles</td>
<td style="text-align: left;">Armstrong-CCM Motorcycles</td>
<td style="text-align: left;">Armstrong-CCM Motorcycles</td>
<td style="text-align: left;">Armstrong-CCM Motorcycles — was a motorcycle manufacturer from 1980 to 1987. Headquartered in Bolton, it was formerly known as Clews Competition Motorcycles.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Arrival (company)</td>
<td style="text-align: left;">/wiki/Arrival_(company)</td>
<td style="text-align: left;">Arrival</td>
<td style="text-align: left;">Arrival</td>
<td style="text-align: left;">Arrival — is an electric vehicle manufacturer, specialising in commercial vehicles. Established in 2015, its headquarters is in Yarnton, Oxfordshire. It was formerly named Charge Automotive.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Arrol-Johnston</td>
<td style="text-align: left;">/wiki/Arrol-Johnston</td>
<td style="text-align: left;">Arrol-Johnston</td>
<td style="text-align: left;">Arrol-Johnston</td>
<td style="text-align: left;">Arrol-Johnston — was an automobile manufacturer from 1895 to 1931. Its headquarters was in Glasgow, Scotland. It was formerly the Mo-Car Syndicate. In 1927 it merged with Aster to become Arrol-Aster.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Arrol-Aster</td>
<td style="text-align: left;">/wiki/Arrol-Aster</td>
<td style="text-align: left;">Arrol-Aster</td>
<td style="text-align: left;">Arrol-Aster</td>
<td style="text-align: left;">Arrol-Aster — was an automobile manufacturer from 1927 to 1931. Headquartered in Dumfries, Scotland, it was formed by the merger of Arrol-Johnston and Aster.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Ascari Cars</td>
<td style="text-align: left;">/wiki/Ascari_Cars</td>
<td style="text-align: left;">Ascari Cars</td>
<td style="text-align: left;">Ascari Cars</td>
<td style="text-align: left;">Ascari Cars — was an automobile manufacturer from 1995 to 2010. Its headquarters was in Banbury, Oxfordshire.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Asda</td>
<td style="text-align: left;">/wiki/Asda</td>
<td style="text-align: left;">Asda Stores</td>
<td style="text-align: left;">Asda Stores</td>
<td style="text-align: left;">Asda Stores - is a supermarket chain also offering some financial services, and a mobile phone virtual network through its subsidiary Asda Mobile. Established in 1949, its headquarters is in Leeds. In 1999 it was acquired by Walmart, then in 2021 it was acquired by EG Group and TDR Capital. Its 2019 revenue was £22.8 billion, with an operating profit of £584.2 million.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Associated British Picture Corporation</td>
<td style="text-align: left;">/wiki/Associated_British_Picture_Corporation</td>
<td style="text-align: left;">Associated British Picture Corporation</td>
<td style="text-align: left;">Associated British Picture Corporation</td>
<td style="text-align: left;">Associated British Picture Corporation (ABPC) — was a film production, distribution, and exhibition company from 1927 to 1970. It was originally British International Pictures (BIC).</td>
</tr>
<tr class="even">
<td style="text-align: left;">Associated Motor Cycles</td>
<td style="text-align: left;">/wiki/Associated_Motor_Cycles</td>
<td style="text-align: left;">Associated Motor Cycles</td>
<td style="text-align: left;">Associated Motor Cycles</td>
<td style="text-align: left;">Associated Motor Cycles — was the parent company of motorcycle companies including: Matchless, A. J. Stevens &amp; Co. Francis-Barnett, James Cycle Co, Norton, and Sunbeam, from 1938 to 1966.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Aster (automobile)</td>
<td style="text-align: left;">/wiki/Aster_(automobile)</td>
<td style="text-align: left;">Aster</td>
<td style="text-align: left;">Aster</td>
<td style="text-align: left;">Aster — was an automobile, and aircraft engines manufacturer from 1913 to 1931. It was headquartered in Wembley, London, then Dumfries, Scotland. It was formerly Begbie Engineering. In 1927 it merged with Arrol-Johnston.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Astley and Tyldesley Collieries</td>
<td style="text-align: left;">/wiki/Astley_and_Tyldesley_Collieries#History</td>
<td style="text-align: left;">Astley and Bedford Collieries</td>
<td style="text-align: left;">Astley and Bedford Collieries</td>
<td style="text-align: left;">Astley and Bedford Collieries — was a coal mining company from the 1840s to the 1850s. Its headquarters was in Bedford, Leigh.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Astley and Tyldesley Collieries</td>
<td style="text-align: left;">/wiki/Astley_and_Tyldesley_Collieries</td>
<td style="text-align: left;">Astley and Tyldesley Collieries</td>
<td style="text-align: left;">Astley and Tyldesley Collieries</td>
<td style="text-align: left;">Astley and Tyldesley Collieries — was a coal mining company from 1900 to 1929. It became part of Manchester Collieries.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Aston Martin</td>
<td style="text-align: left;">/wiki/Aston_Martin</td>
<td style="text-align: left;">Aston Martin</td>
<td style="text-align: left;">Aston Martin</td>
<td style="text-align: left;">Aston Martin — is a manufacturer of automobiles, luxury goods, and previously aircraft components during WWII. Established in 1913, its headquarters is in Gaydon, Warwickshire. Its 2019 revenue was £997 million, with net income of –£104 million.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Astra Films</td>
<td style="text-align: left;">/wiki/Astra_Films</td>
<td style="text-align: left;">Astra Films</td>
<td style="text-align: left;">Astra Films</td>
<td style="text-align: left;">Astra Films — is a film production and distribution company. Its headquarters is in Leeds, Yorkshire.</td>
</tr>
<tr class="even">
<td style="text-align: left;">AstraZeneca</td>
<td style="text-align: left;">/wiki/AstraZeneca</td>
<td style="text-align: left;">AstraZeneca</td>
<td style="text-align: left;">AstraZeneca</td>
<td style="text-align: left;">AstraZeneca — is a UK-Swedish multinational pharmaceutical and biopharmaceutical company. Established in 1999, its headquarters is in Cambridge. It was formed by the merger of Astra AB and Zeneca. Its 2019 revenue was $24.3 billion, with net income of $1.2 billion.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Ausfod</td>
<td style="text-align: left;">/wiki/Ausfod</td>
<td style="text-align: left;">Ausfod</td>
<td style="text-align: left;">Ausfod</td>
<td style="text-align: left;">Ausfod — was an automobile manufacturer from 1947 to 1948. Its headquarters was in Chorlton-on-Medlock, Manchester.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Aura Films</td>
<td style="text-align: left;">/wiki/Aura_Films</td>
<td style="text-align: left;">Aura Films</td>
<td style="text-align: left;">Aura Films</td>
<td style="text-align: left;">Aura Films — is a film production company. Established in 2011, its headquarters is in Colchester, Essex.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Austin-Healey</td>
<td style="text-align: left;">/wiki/Austin-Healey</td>
<td style="text-align: left;">Austin-Healey</td>
<td style="text-align: left;">Austin-Healey</td>
<td style="text-align: left;">Austin-Healey — was an automobile manufacturer from 1952 to 1972. It was established as a joint venture between British Motor Corporation and Donald Healey Motor Company.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Austin Motor Company</td>
<td style="text-align: left;">/wiki/Austin_Motor_Company</td>
<td style="text-align: left;">Austin Motor Company</td>
<td style="text-align: left;">Austin Motor Company</td>
<td style="text-align: left;">Austin Motor Company — was a manufacturer of automobiles, and wartime manufacturer of aircraft, shells, heavy guns and military vehicles from 1905 to 1952. Its headquarters was in Longbridge, Birmingham. In 1952 it merged with Morris Motors to become the British Motor Corporation.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Austin Rover Group</td>
<td style="text-align: left;">/wiki/Austin_Rover_Group</td>
<td style="text-align: left;">Austin Rover Group</td>
<td style="text-align: left;">Austin Rover Group</td>
<td style="text-align: left;">Austin Rover Group — was an automobile manufacturer from 1982 to 1989. Headquartered in Longbridge, Birmingham, it was a subsidiary of British Leyland. 1n 1989 it became Rover Group.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Auto-Sleepers</td>
<td style="text-align: left;">/wiki/Auto-Sleepers</td>
<td style="text-align: left;">Auto-Sleepers</td>
<td style="text-align: left;">Auto-Sleepers</td>
<td style="text-align: left;">Auto-Sleepers — is a camper van motor homes manufacturer. Established in 1961, its headquarters is in Willersey, Gloucestershire.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Axon Automotive</td>
<td style="text-align: left;">/wiki/Axon_Automotive</td>
<td style="text-align: left;">Axon Automotive</td>
<td style="text-align: left;">Axon Automotive</td>
<td style="text-align: left;">Axon Automotive — is an automobile and components manufacturer. Its headquarters is in Northampton, Northamptonshire.</td>
</tr>
<tr class="even">
<td style="text-align: left;">B&amp;M</td>
<td style="text-align: left;">/wiki/B%26M</td>
<td style="text-align: left;">B&amp;M European Value Retail</td>
<td style="text-align: left;">B&amp;M European Value Retail</td>
<td style="text-align: left;">B&amp;M European Value Retail - is a variety store chain including B&amp;M Bargains, and B&amp;M Homestore. Established in 1978 as Billington &amp; Mayman, its headquarters are in Speke, Liverpool (operations) and Luxembourg (registration). Heron Foods is its subsidiary company. In 2020 its revenue was £3.8 billion, with net income of £80.9 million.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">BAE Systems</td>
<td style="text-align: left;">/wiki/BAE_Systems</td>
<td style="text-align: left;">BAE Systems</td>
<td style="text-align: left;">BAE Systems</td>
<td style="text-align: left;">BAE Systems — is a British multinational defence, security, and aerospace company (civil and military aircraft, defence electronics, naval vessels, munitions, and land warfare systems). Established in 1999, its headquarters are in London, and Farnborough, Hampshire. It was formed from the merger of British Aerospace and Marconi Electronic Systems. In 2019 its revenue was £18.3 billion, with net income of £1.5 billion.</td>
</tr>
<tr class="even">
<td style="text-align: left;">BAE Systems Applied Intelligence</td>
<td style="text-align: left;">/wiki/BAE_Systems_Applied_Intelligence</td>
<td style="text-align: left;">BAE Systems Applied Intelligence</td>
<td style="text-align: left;">BAE Systems Applied Intelligence</td>
<td style="text-align: left;">BAE Systems Applied Intelligence — is an international business and consulting company (cyber security and cyber intelligence). Established in 1971, its headquarters is in Guildford, Surrey. It was formally known as Smith Associates, and Detica. Its parent company is BAE Systems.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Baillie Gifford</td>
<td style="text-align: left;">/wiki/Baillie_Gifford</td>
<td style="text-align: left;">Baillie Gifford &amp; Co</td>
<td style="text-align: left;">Baillie Gifford &amp; Co</td>
<td style="text-align: left;">Baillie Gifford &amp; Co — is an investment management company. Established in 1908, its headquarters is in Edinburgh, Scotland. It manages the Scottish Mortgage Investment Trust.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Bamforth &amp; Co Ltd</td>
<td style="text-align: left;">/wiki/Bamforth_%26_Co_Ltd</td>
<td style="text-align: left;">Bamforth &amp; Co Ltd</td>
<td style="text-align: left;">Bamforth &amp; Co Ltd</td>
<td style="text-align: left;">Bamforth &amp; Co Ltd - film production, and publishing (postcards) company. Established in 1870 in Holmfirth, Yorkshire, its headquarters is now in Leeds, Yorkshire.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Bank of Scotland</td>
<td style="text-align: left;">/wiki/Bank_of_Scotland</td>
<td style="text-align: left;">Bank of Scotland</td>
<td style="text-align: left;">Bank of Scotland</td>
<td style="text-align: left;">Bank of Scotland — financial services company (banking, insurance, and banknote production). Established in 1695, its headquarters is at The Mound, Edinburgh, Scotland. It was previously part of HBOS. Its parent company is Lloyds Banking Group.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Banks Group</td>
<td style="text-align: left;">/wiki/Banks_Group</td>
<td style="text-align: left;">Banks Group</td>
<td style="text-align: left;">Banks Group</td>
<td style="text-align: left;">Banks Group — mining, energy, and property development company. Established in 1976, its headquarters is in Durham.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Banter Media</td>
<td style="text-align: left;">/wiki/Banter_Media</td>
<td style="text-align: left;">Banter Media</td>
<td style="text-align: left;">Banter Media</td>
<td style="text-align: left;">Banter Media — new media, music recording, and film production company. Established in 2009, its headquarters is in Manchester.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Barclays</td>
<td style="text-align: left;">/wiki/Barclays</td>
<td style="text-align: left;">Barclays plc</td>
<td style="text-align: left;">Barclays plc</td>
<td style="text-align: left;">Barclays plc — financial services company (banking, investment management, and wealth management). Established in 1690, its headquarters is in London. In 2019 its revenue was £21.6 billion, with a net income of £3.3 billion.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">BBC</td>
<td style="text-align: left;">/wiki/BBC</td>
<td style="text-align: left;">BBC</td>
<td style="text-align: left;">BBC</td>
<td style="text-align: left;">BBC (British Broadcasting Corporation) — public service broadcasting statutory corporation (television and radio broadcasting, online services). Established in 1922, its headquarters is at Broadcasting House, London. It was first formed as the British Broadcasting Company. In 2019 its revenue was £4.8 billion, with a net income of -£69 million.</td>
</tr>
<tr class="even">
<td style="text-align: left;">BBC Films</td>
<td style="text-align: left;">/wiki/BBC_Films</td>
<td style="text-align: left;">BBC Films</td>
<td style="text-align: left;">BBC Films</td>
<td style="text-align: left;">BBC Films — film production company. Established in 1990, its headquarters is in London. Its parent company is the BBC.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">BBC Studios</td>
<td style="text-align: left;">/wiki/BBC_Studios</td>
<td style="text-align: left;">BBC Studios</td>
<td style="text-align: left;">BBC Studios</td>
<td style="text-align: left;">BBC Studios — television production and distribution company. Established in 2015, its headquarters is at Television Centre, London. In 2018 it subsumed BBC Worldwide. Its parent company is the BBC.</td>
</tr>
<tr class="even">
<td style="text-align: left;">BBC Studioworks</td>
<td style="text-align: left;">/wiki/BBC_Studioworks</td>
<td style="text-align: left;">BBC Studioworks</td>
<td style="text-align: left;">BBC Studioworks</td>
<td style="text-align: left;">BBC Studioworks — television studios, post-production, and related services company. Established in 1998, its headquarters is in London. Formerly known as BBC Resources Limited, and BBC Studios and Post Production Limited, its parent company is the BBC.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Beauford automobiles</td>
<td style="text-align: left;">/wiki/Beauford_automobiles</td>
<td style="text-align: left;">Beauford automobiles</td>
<td style="text-align: left;">Beauford automobiles</td>
<td style="text-align: left;">Beauford automobiles — car kit manufacturing company. Established in Up Holland, its headquarters is in Stoke-on-Trent.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Bede Gaming</td>
<td style="text-align: left;">/wiki/Bede_Gaming</td>
<td style="text-align: left;">Bede Gaming</td>
<td style="text-align: left;">Bede Gaming</td>
<td style="text-align: left;">Bede Gaming — software, and gambling company. Established in 2011, its headquarters is in Newcastle upon Tyne.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Bedford Colliery</td>
<td style="text-align: left;">/wiki/Bedford_Colliery</td>
<td style="text-align: left;">Bedford Colliery</td>
<td style="text-align: left;">Bedford Colliery</td>
<td style="text-align: left;">Bedford Colliery — coal mine, c1874–1929. Located in Bedford, Leigh, it became part of Manchester Collieries.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Bedlam Productions</td>
<td style="text-align: left;">/wiki/Bedlam_Productions</td>
<td style="text-align: left;">Bedlam Productions</td>
<td style="text-align: left;">Bedlam Productions</td>
<td style="text-align: left;">Bedlam Productions — film and TV production company. Established in 2009, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Beecham Group</td>
<td style="text-align: left;">/wiki/Beecham_Group</td>
<td style="text-align: left;">Beecham Group</td>
<td style="text-align: left;">Beecham Group</td>
<td style="text-align: left;">Beecham Group — manufacturing company (pharmaceuticals, drinks, toothpaste, and men’s grooming products) 1859–1989. Its headquarters was in London. In 1989 Beecham Group and SmithKline Beckman merged to form SmithKline Beecham, and in 2000, they merged with GlaxoWellcome to form GlaxoSmithKline.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Beefeater (restaurant)</td>
<td style="text-align: left;">/wiki/Beefeater_(restaurant)</td>
<td style="text-align: left;">Beefeater</td>
<td style="text-align: left;">Beefeater</td>
<td style="text-align: left;">Beefeater — hospitality company (licensed restaurant chain). Established in 1974, its headquarters is in Dunstable, Bedfordshire. Its parent company is Whitbread.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Bell Pottinger</td>
<td style="text-align: left;">/wiki/Bell_Pottinger</td>
<td style="text-align: left;">Bell Pottinger</td>
<td style="text-align: left;">Bell Pottinger</td>
<td style="text-align: left;">Bell Pottinger — public relations, and advertising company, 1988–2017. Its headquarters was in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Bentley</td>
<td style="text-align: left;">/wiki/Bentley</td>
<td style="text-align: left;">Bentley</td>
<td style="text-align: left;">Bentley</td>
<td style="text-align: left;">Bentley — automobile manufacturing company (luxury cars and racing cars). Established in 1919 in London, its headquarters is in Crewe. Between 1931 and 1970 it was owned by Rolls-Royce. From 1980 to 1998 it was owned by Vickers. From 1998 it is owned by Volkswagen.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Beowulf Mining</td>
<td style="text-align: left;">/wiki/Beowulf_Mining</td>
<td style="text-align: left;">Beowulf Mining</td>
<td style="text-align: left;">Beowulf Mining</td>
<td style="text-align: left;">Beowulf Mining — mining company (exploration and development). Established in 1978, it was formerly known as Beowulf Gold.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Bet365</td>
<td style="text-align: left;">/wiki/Bet365</td>
<td style="text-align: left;">bet365</td>
<td style="text-align: left;">bet365</td>
<td style="text-align: left;">bet365 — online gambling company. Established in 2000, its headquarters is in Stoke-on-Trent.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Betable</td>
<td style="text-align: left;">/wiki/Betable</td>
<td style="text-align: left;">Betable</td>
<td style="text-align: left;">Betable</td>
<td style="text-align: left;">Betable — gambling, and social gaming company. Established in 2008, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Betfair</td>
<td style="text-align: left;">/wiki/Betfair</td>
<td style="text-align: left;">Betfair</td>
<td style="text-align: left;">Betfair</td>
<td style="text-align: left;">Betfair — online gambling company. Established in 2000, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Betfred</td>
<td style="text-align: left;">/wiki/Betfred</td>
<td style="text-align: left;">Betfred</td>
<td style="text-align: left;">Betfred</td>
<td style="text-align: left;">Betfred — gambling company. Established in 1967 in Salford, its headquarters is in Warrington.</td>
</tr>
<tr class="even">
<td style="text-align: left;">BetonSports</td>
<td style="text-align: left;">/wiki/BetonSports</td>
<td style="text-align: left;">BetonSports</td>
<td style="text-align: left;">BetonSports</td>
<td style="text-align: left;">BetonSports — online gambling company. Established in 1995, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">BFCS</td>
<td style="text-align: left;">/wiki/BFCS</td>
<td style="text-align: left;">BFCS</td>
<td style="text-align: left;">BFCS</td>
<td style="text-align: left;">BFCS — commercials film production company, 1966–2001. Headquartered in London, it was first named Brooks Baker Fulford.</td>
</tr>
<tr class="even">
<td style="text-align: left;">BHP</td>
<td style="text-align: left;">/wiki/BHP</td>
<td style="text-align: left;">BHP</td>
<td style="text-align: left;">BHP</td>
<td style="text-align: left;">BHP — Anglo/Australian multinational mining, metals, and petroleum company. Established in 1885, its headquarters are in Melbourne, Australia and London. It was formerly known as BHP Billiton.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Big Talk Productions</td>
<td style="text-align: left;">/wiki/Big_Talk_Productions</td>
<td style="text-align: left;">Big Talk Productions</td>
<td style="text-align: left;">Big Talk Productions</td>
<td style="text-align: left;">Big Talk Productions — film and TV production company. Established in 1994, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Bigballs Media</td>
<td style="text-align: left;">/wiki/Bigballs_Media</td>
<td style="text-align: left;">Bigballs Media</td>
<td style="text-align: left;">Bigballs Media</td>
<td style="text-align: left;">Bigballs Media — football media company. Established in 2006, its headquarters is in London. It is now named Copa90.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Biocompatibles</td>
<td style="text-align: left;">/wiki/Biocompatibles</td>
<td style="text-align: left;">Biocompatibles</td>
<td style="text-align: left;">Biocompatibles</td>
<td style="text-align: left;">Biocompatibles — pharmaceutical company (drug eluting beads, radiation delivering seeds). Established in 1984, its headquarters is in Farnham, Surrey. In 2010 it was acquired by BTG plc.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Bio Products Laboratory</td>
<td style="text-align: left;">/wiki/Bio_Products_Laboratory</td>
<td style="text-align: left;">Bio Products Laboratory</td>
<td style="text-align: left;">Bio Products Laboratory</td>
<td style="text-align: left;">Bio Products Laboratory — pharmaceuticals company (human blood plasma products). Established in 1954 in Elstree. It was formerly part of the NHS; but is now owned by Creat Group.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Birmingham and Staffordshire Gas Light Company</td>
<td style="text-align: left;">/wiki/Birmingham_and_Staffordshire_Gas_Light_Company</td>
<td style="text-align: left;">Birmingham and Staffordshire Gas Light Company</td>
<td style="text-align: left;">Birmingham and Staffordshire Gas Light Company</td>
<td style="text-align: left;">Birmingham and Staffordshire Gas Light Company — gas production and supply company, 1825–1875.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Birmingham Gas Light and Coke Company</td>
<td style="text-align: left;">/wiki/Birmingham_Gas_Light_and_Coke_Company</td>
<td style="text-align: left;">Birmingham Gas Light and Coke Company</td>
<td style="text-align: left;">Birmingham Gas Light and Coke Company</td>
<td style="text-align: left;">Birmingham Gas Light and Coke Company — gas production and supply company, 1819–1875.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Birmingham Midshires</td>
<td style="text-align: left;">/wiki/Birmingham_Midshires</td>
<td style="text-align: left;">Birmingham Midshires</td>
<td style="text-align: left;">Birmingham Midshires</td>
<td style="text-align: left;">Birmingham Midshires — financial services company (banking and insurance). It was formerly a building society. Established in 1986, its headquarters is in Wolverhampton. It was formed by the merger of the Birmingham and Bridgwater Building Society with the Midshires Building Society. It has become a division of Lloyds Banking Group.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Bisichi Mining</td>
<td style="text-align: left;">/wiki/Bisichi_Mining</td>
<td style="text-align: left;">Bisichi Mining</td>
<td style="text-align: left;">Bisichi Mining</td>
<td style="text-align: left;">Bisichi Mining — mining and property corporation. Established in 1910, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Black Camel Pictures</td>
<td style="text-align: left;">/wiki/Black_Camel_Pictures</td>
<td style="text-align: left;">Black Camel Pictures</td>
<td style="text-align: left;">Black Camel Pictures</td>
<td style="text-align: left;">Black Camel Pictures — film production company. Its headquarters is in Glasgow, Scotland.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Mancunian Films</td>
<td style="text-align: left;">/wiki/Mancunian_Films</td>
<td style="text-align: left;">Mancunian Films</td>
<td style="text-align: left;">Mancunian Films</td>
<td style="text-align: left;">Blakeley’s Productions - film production company. See Mancunian Films.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Bleep.com</td>
<td style="text-align: left;">/wiki/Bleep.com</td>
<td style="text-align: left;">Bleep</td>
<td style="text-align: left;">Bleep</td>
<td style="text-align: left;">Bleep — online record store company. Created by Warp Records), it was established in 2004.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Blink (company)</td>
<td style="text-align: left;">/wiki/Blink_(company)</td>
<td style="text-align: left;">Blink</td>
<td style="text-align: left;">Blink</td>
<td style="text-align: left;">Blink — advertising, and music videos company. Established in 1985, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Blueprint Pictures</td>
<td style="text-align: left;">/wiki/Blueprint_Pictures</td>
<td style="text-align: left;">Blueprint Pictures</td>
<td style="text-align: left;">Blueprint Pictures</td>
<td style="text-align: left;">Blueprint Pictures — film production company. Established in 2005, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Bolexbrothers</td>
<td style="text-align: left;">/wiki/Bolexbrothers</td>
<td style="text-align: left;">bolexbrothers</td>
<td style="text-align: left;">bolexbrothers</td>
<td style="text-align: left;">bolexbrothers — animation film production company. Established in 1993, its headquarters is in Bristol.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Bolckow, Vaughan</td>
<td style="text-align: left;">/wiki/Bolckow,_Vaughan</td>
<td style="text-align: left;">Bolckow, Vaughan</td>
<td style="text-align: left;">Bolckow, Vaughan</td>
<td style="text-align: left;">Bolckow, Vaughan — mining, ironmaking, and steel production company, 1840–1929. Its headquarters was in Middlesbrough.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Bolsover Colliery Company</td>
<td style="text-align: left;">/wiki/Bolsover_Colliery_Company</td>
<td style="text-align: left;">Bolsover Colliery Company</td>
<td style="text-align: left;">Bolsover Colliery Company</td>
<td style="text-align: left;">Bolsover Colliery Company — coal mining company, 1889–1947. Headquartered in Bolsover, Derbyshire, in 1947 it was nationalised and became part of the National Coal Board.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Boots UK</td>
<td style="text-align: left;">/wiki/Boots_UK</td>
<td style="text-align: left;">Boots UK</td>
<td style="text-align: left;">Boots UK</td>
<td style="text-align: left;">Boots UK — pharmaceutical retailer and manufacturer, health and beauty, and photography company. Established in 1849, its headquarters is in Nottingham. It was formerly known as Boots the Chemists, and Boots Pure Drugs Company. Since 2014 it is a subsidiary of Walgreens Boots Alliance.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Bourne Leisure</td>
<td style="text-align: left;">/wiki/Bourne_Leisure</td>
<td style="text-align: left;">Bourne Leisure</td>
<td style="text-align: left;">Bourne Leisure</td>
<td style="text-align: left;">Bourne Leisure — leisure company (caravan parks, holiday camps, hotels). Established in 1964 in Whitstable, its headquarters is in Hemel Hempstead, Hertfordshire.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Bournemouth Water</td>
<td style="text-align: left;">/wiki/Bournemouth_Water</td>
<td style="text-align: left;">Bournemouth Water</td>
<td style="text-align: left;">Bournemouth Water</td>
<td style="text-align: left;">Bournemouth Water — utility company (water supply). Established in 1863, its headquarters is in Bournemouth, Dorset. Its parent company is South West Water which is owned by the Pennon Group.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Bowler Manufacturing</td>
<td style="text-align: left;">/wiki/Bowler_Manufacturing</td>
<td style="text-align: left;">Bowler Manufacturing</td>
<td style="text-align: left;">Bowler Manufacturing</td>
<td style="text-align: left;">Bowler Manufacturing — automobile manufacturing company (off-road). Established in 1985, its headquarters is in Belper, Derbyshire.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Bradford &amp; Bingley</td>
<td style="text-align: left;">/wiki/Bradford_%26_Bingley</td>
<td style="text-align: left;">Bradford &amp; Bingley</td>
<td style="text-align: left;">Bradford &amp; Bingley</td>
<td style="text-align: left;">Bradford &amp; Bingley — financial services company (banking), 1964–2010. Formerly a building society, its headquarters was in Bingley, West Yorkshire. It was formed by the merger of the Bradford Equitable Building Society with the Bingley Permanent Building Society. It was nationalised in 2008, and in 2010 the savings business was subsumed by Santander Group, while the mortgage business was merged with Northern Rock (asset management) to form UK Asset Resolution.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Brazil Iron</td>
<td style="text-align: left;">/wiki/Brazil_Iron</td>
<td style="text-align: left;">Brazil Iron</td>
<td style="text-align: left;">Brazil Iron</td>
<td style="text-align: left;">Brazil Iron — metals and mining company. Established in 2000, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Brewers Fayre</td>
<td style="text-align: left;">/wiki/Brewers_Fayre</td>
<td style="text-align: left;">Brewers Fayre</td>
<td style="text-align: left;">Brewers Fayre</td>
<td style="text-align: left;">Brewers Fayre — hospitality company (licensed restaurant chain). Established in 1979, its headquarters is in Dunstable, Bedfordshire. Its parent company is Whitbread.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Bridgewater Collieries</td>
<td style="text-align: left;">/wiki/Bridgewater_Collieries</td>
<td style="text-align: left;">Bridgewater Collieries</td>
<td style="text-align: left;">Bridgewater Collieries</td>
<td style="text-align: left;">Bridgewater Collieries — coal mining company, 1921–1929. It became part of Manchester Collieries.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Briggs Automotive Company</td>
<td style="text-align: left;">/wiki/Briggs_Automotive_Company</td>
<td style="text-align: left;">Briggs Automotive Company</td>
<td style="text-align: left;">Briggs Automotive Company</td>
<td style="text-align: left;">Briggs Automotive Company — automobile manufacturing company (sports cars). Established in 2009, its headquarters is in Speke, Liverpool.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Bristol Water</td>
<td style="text-align: left;">/wiki/Bristol_Water</td>
<td style="text-align: left;">Bristol Water</td>
<td style="text-align: left;">Bristol Water</td>
<td style="text-align: left;">Bristol Water — utility company (water supply). Established in 1846, its headquarters is in Bristol. It was formerly known as the Bristol Waterworks Company.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">British Aerospace</td>
<td style="text-align: left;">/wiki/British_Aerospace</td>
<td style="text-align: left;">British Aerospace</td>
<td style="text-align: left;">British Aerospace</td>
<td style="text-align: left;">British Aerospace — aircraft, munitions, and defence systems manufacturing company, 1977–1999 (also automobile production 1988–1994). Its headquarters was in Farnborough, Hampshire. It was formed from the nationalisation and merger of the British Aircraft Corporation, Hawker Siddeley Aviation, Hawker Siddeley Dynamics, and Scottish Aviation. In 1999 it was merged with Marconi Electronic Systems to form BAE Systems.</td>
</tr>
<tr class="even">
<td style="text-align: left;">British Airways</td>
<td style="text-align: left;">/wiki/British_Airways</td>
<td style="text-align: left;">British Airways</td>
<td style="text-align: left;">British Airways</td>
<td style="text-align: left;">British Airways — airline company. Established in 1974, its headquarters is Waterside, Harmondsworth. It was formed from the merger of British Overseas Airways Corporation, British European Airways, Cambrian Airways and Northeast Airlines. Its parent company is International Airlines Group.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">British Aluminium</td>
<td style="text-align: left;">/wiki/British_Aluminium</td>
<td style="text-align: left;">British Aluminium</td>
<td style="text-align: left;">British Aluminium</td>
<td style="text-align: left;">British Aluminium — aluminium production company, 1894–2007. It was also known as British Alcan Aluminium.</td>
</tr>
<tr class="even">
<td style="text-align: left;">British American Tobacco</td>
<td style="text-align: left;">/wiki/British_American_Tobacco</td>
<td style="text-align: left;">British American Tobacco</td>
<td style="text-align: left;">British American Tobacco</td>
<td style="text-align: left;">British American Tobacco — cigarette and tobacco manufacturing company (previously also retailing, and financial services). Established in 1902, its headquarters is in London. It was formed when the Imperial Tobacco Company and the American Tobacco Company created a joint venture, the British-American Tobacco Company. Its 2019 revenue was £25.8 billion, with net income of £1.8 billion.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">British and Colonial Films</td>
<td style="text-align: left;">/wiki/British_and_Colonial_Films</td>
<td style="text-align: left;">British and Colonial Films</td>
<td style="text-align: left;">British and Colonial Films</td>
<td style="text-align: left;">British and Colonial Films — film production company, 1908–1924. Headquartered in London, it was first named British and Colonial Kinematograph Company.</td>
</tr>
<tr class="even">
<td style="text-align: left;">British and Dominions Film Corporation</td>
<td style="text-align: left;">/wiki/British_and_Dominions_Film_Corporation</td>
<td style="text-align: left;">British and Dominions Film Corporation</td>
<td style="text-align: left;">British and Dominions Film Corporation</td>
<td style="text-align: left;">British and Dominions Film Corporation — film production company, 1929–1936. Its headquarters was in Borehamwood, Hertfordshire.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">British Biotech</td>
<td style="text-align: left;">/wiki/British_Biotech</td>
<td style="text-align: left;">British Biotech</td>
<td style="text-align: left;">British Biotech</td>
<td style="text-align: left;">British Biotech — biotechnology company (pharmaceuticals) 1986–2003. Its headquarters was in Oxford. In 2003 it was merged into Ribo Targets and then into Vernalis plc.</td>
</tr>
<tr class="even">
<td style="text-align: left;">British Coal</td>
<td style="text-align: left;">/wiki/British_Coal</td>
<td style="text-align: left;">British Coal</td>
<td style="text-align: left;">British Coal</td>
<td style="text-align: left;">British Coal — nationalised coal mining corporation, 1946–1997. It was formerly known as The National Coal Board. It was privatised and succeeded by UK Coal.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">British Energy</td>
<td style="text-align: left;">/wiki/British_Energy</td>
<td style="text-align: left;">British Energy</td>
<td style="text-align: left;">British Energy</td>
<td style="text-align: left;">British Energy — energy company (electricity generation), 1995–2009. Its headquarters was in London. It was acquired and subsumed by Electricite de France (EDF).</td>
</tr>
<tr class="even">
<td style="text-align: left;">British Gas Corporation</td>
<td style="text-align: left;">/wiki/British_Gas_Corporation</td>
<td style="text-align: left;">British Gas Corporation</td>
<td style="text-align: left;">British Gas Corporation</td>
<td style="text-align: left;">British Gas Corporation — state owned energy company (gas supplier and distributor), 1972–1986. It was formed from the 12 regional gas boards. In 1986 it was privatised to become British Gas plc.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">British Gas plc</td>
<td style="text-align: left;">/wiki/British_Gas_plc</td>
<td style="text-align: left;">British Gas plc</td>
<td style="text-align: left;">British Gas plc</td>
<td style="text-align: left;">British Gas plc — energy supplier (gas), and home services company, 1986–1997. It was formed from the privatisation of the British Gas Corporation. In 1997 it was demerged into Centrica, BG Group, and Transco.</td>
</tr>
<tr class="even">
<td style="text-align: left;">British Instructional Films</td>
<td style="text-align: left;">/wiki/British_Instructional_Films</td>
<td style="text-align: left;">British Instructional Films</td>
<td style="text-align: left;">British Instructional Films</td>
<td style="text-align: left;">British Instructional Films — film production company, 1919–1932.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Associated British Picture Corporation</td>
<td style="text-align: left;">/wiki/Associated_British_Picture_Corporation</td>
<td style="text-align: left;">Associated British Picture Corporation</td>
<td style="text-align: left;">Associated British Picture Corporation</td>
<td style="text-align: left;">British International Pictures — film production, distribution, and exhibition company. See Associated British Picture Corporation.</td>
</tr>
<tr class="even">
<td style="text-align: left;">British Land</td>
<td style="text-align: left;">/wiki/British_Land</td>
<td style="text-align: left;">British Land</td>
<td style="text-align: left;">British Land</td>
<td style="text-align: left;">British Land — real estate company (property development and investment). Established in 1856, its headquarters is in London. It was formed as an offshoot of the National Freehold Land Society. In 2019 its revenue was £554 million, with net income of £320 million.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">British Leyland</td>
<td style="text-align: left;">/wiki/British_Leyland</td>
<td style="text-align: left;">British Leyland</td>
<td style="text-align: left;">British Leyland</td>
<td style="text-align: left;">British Leyland — automobile manufacturing and engineering company, 1965–1986. Its headquarters were in Longbridge, Birmingham, and Cowley, Oxfordshire. Also known as BLMC Ltd, it was first established with the merger of Leyland Motors, and British Motor Holdings. In 1986 it was renamed as The Rover Group, and later as MG Rover Group.</td>
</tr>
<tr class="even">
<td style="text-align: left;">British Lion Films</td>
<td style="text-align: left;">/wiki/British_Lion_Films</td>
<td style="text-align: left;">British Lion Films</td>
<td style="text-align: left;">British Lion Films</td>
<td style="text-align: left;">British Lion Films — film production and distribution company. Established in 1919, it was first named British Lion Film Corporation Ltd.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">British Steel Limited</td>
<td style="text-align: left;">/wiki/British_Steel_Limited</td>
<td style="text-align: left;">British Steel Limited</td>
<td style="text-align: left;">British Steel Limited</td>
<td style="text-align: left;">British Steel Limited — steel company (long steel products). Established in 2016, it was formed from the sale of long steel production by Tata Steel Europe to Greybull Capital. Its parent company is Jingye Group.</td>
</tr>
<tr class="even">
<td style="text-align: left;">British Steel plc</td>
<td style="text-align: left;">/wiki/British_Steel_plc</td>
<td style="text-align: left;">British Steel plc</td>
<td style="text-align: left;">British Steel plc</td>
<td style="text-align: left;">British Steel plc — steel production company, 1967–1999. Formerly known as the British Steel Corporation, it was formed from the nationalisation of 14 private steel companies. It was privatised in 1988, and in 1999 it was merged with Koninklijke Hoogovens to form Corus Group.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">G.B. Samuelson Productions</td>
<td style="text-align: left;">/wiki/G.B._Samuelson_Productions</td>
<td style="text-align: left;">G.B. Samuelson Productions</td>
<td style="text-align: left;">G.B. Samuelson Productions</td>
<td style="text-align: left;">British Super Films — film production company. See G.B. Samuelson Productions.</td>
</tr>
<tr class="even">
<td style="text-align: left;">British Transport Films</td>
<td style="text-align: left;">/wiki/British_Transport_Films</td>
<td style="text-align: left;">British Transport Films</td>
<td style="text-align: left;">British Transport Films</td>
<td style="text-align: left;">British Transport Films — documentary film production company. It was established in 1949.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Britannia Building Society</td>
<td style="text-align: left;">/wiki/Britannia_Building_Society</td>
<td style="text-align: left;">Britannia Building Society</td>
<td style="text-align: left;">Britannia Building Society</td>
<td style="text-align: left;">Britannia Building Society — mutual building society (savings and mortgages), 1856–2009. Its headquarters was in Leek, Staffordshire. It was formed as the Leek and Morlands Permanent Benefit Building Society. Through a series of mergers it later became the Leek and Westbourne, the Westbourne and Eastern Counties, and in 1975 the Britannia Building Society. In 2009 it was merged into The Co-operative Banking Group.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Brooke Cars</td>
<td style="text-align: left;">/wiki/Brooke_Cars</td>
<td style="text-align: left;">Brooke Cars</td>
<td style="text-align: left;">Brooke Cars</td>
<td style="text-align: left;">Brooke Cars — automobile manufacturing company (sports cars). Established in 2002, its headquarters is in Honiton, Devon.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Brooke Marine</td>
<td style="text-align: left;">/wiki/Brooke_Marine</td>
<td style="text-align: left;">Brooke Marine</td>
<td style="text-align: left;">Brooke Marine</td>
<td style="text-align: left;">Brooke Marine — ship building company (civilian, commercial, and warships), 1874–1992. It was also an automobile manufacturer from 1901 to 1913, and a car engines manufacturer until 1938. Headquartered in Lowestoft, Suffolk, it was also known as JW Brooke &amp; Co, and Brooke Yachts.</td>
</tr>
<tr class="even">
<td style="text-align: left;">BFCS</td>
<td style="text-align: left;">/wiki/BFCS</td>
<td style="text-align: left;">BFCS</td>
<td style="text-align: left;">BFCS</td>
<td style="text-align: left;">Brooks Baker Fulford — commercials films productions company. See BFCS.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Brown Lloyd James</td>
<td style="text-align: left;">/wiki/Brown_Lloyd_James</td>
<td style="text-align: left;">Brown Lloyd James</td>
<td style="text-align: left;">Brown Lloyd James</td>
<td style="text-align: left;">Brown Lloyd James — public relations company.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Bryanston Films (UK)</td>
<td style="text-align: left;">/wiki/Bryanston_Films_(UK)</td>
<td style="text-align: left;">Bryanston Films (UK)</td>
<td style="text-align: left;">Bryanston Films (UK)</td>
<td style="text-align: left;">Bryanston Films (UK) — film production company, 1959–1963.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">BT Group</td>
<td style="text-align: left;">/wiki/BT_Group</td>
<td style="text-align: left;">BT Group</td>
<td style="text-align: left;">BT Group</td>
<td style="text-align: left;">BT Group — British multinational telecommunications company (fixed line telephony, mobile telephony, broadband internet, digital television). Established in 1969, its headquarters is in London. Formerly known as Post Office Telecommunications, British Telecom, and then trading as BT, it has 7 divisions and 3 subsidiaries. In 2019 its revenue was £23.4 billion, with net income of £2.1 billion.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Bulb Energy</td>
<td style="text-align: left;">/wiki/Bulb_Energy</td>
<td style="text-align: left;">Bulb Energy</td>
<td style="text-align: left;">Bulb Energy</td>
<td style="text-align: left;">Bulb Energy — energy company (electricity and gas supplier). Established in 2013, its headquarters is in London. It was formerly known as Regent Power, and Hanbury Energy.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Bushey Studios</td>
<td style="text-align: left;">/wiki/Bushey_Studios</td>
<td style="text-align: left;">Bushey Studios</td>
<td style="text-align: left;">Bushey Studios</td>
<td style="text-align: left;">Bushey Studios — film studios, 1913–1985. Its headquarters was in Bushey, Hertfordshire.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Business Stream</td>
<td style="text-align: left;">/wiki/Business_Stream</td>
<td style="text-align: left;">Business Stream</td>
<td style="text-align: left;">Business Stream</td>
<td style="text-align: left;">Business Stream — utility company (water and sewage for non-domestic sites). Established in 2006, its headquarters is in Edinburgh, Scotland. Its parent company is Scottish Water.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Butlins</td>
<td style="text-align: left;">/wiki/Butlins</td>
<td style="text-align: left;">Butlins</td>
<td style="text-align: left;">Butlins</td>
<td style="text-align: left;">Butlins — leisure company (holiday camps and hotels). Established in 1936, its headquarters is in Hemel Hempstead. It is owned by Bourne Leisure Holdings Ltd.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Cadbury</td>
<td style="text-align: left;">/wiki/Cadbury</td>
<td style="text-align: left;">Cadbury</td>
<td style="text-align: left;">Cadbury</td>
<td style="text-align: left;">Cadbury - formerly named “Cadburys” and “Cadbury Schweppes” is a British multinational confectionery company. It was established in 1824 by John Cadbury in Birmingham. Its headquarters are now in Uxbridge, London. Cadbury merged with J. S. Fry &amp; Sons in 1919, and with Schweppes in 1969 to form Cadbury Schweppes until Schweppes was demerged in 2008. Cadbury was bought by Kraft Foods Inc. in 2010, and is now a brand of Mondelez International.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Cahoot</td>
<td style="text-align: left;">/wiki/Cahoot</td>
<td style="text-align: left;">cahoot</td>
<td style="text-align: left;">cahoot</td>
<td style="text-align: left;">cahoot — financial services company (online banking). Established in 2000, its headquarters is in Belfast, Northern Ireland. Formerly part of Abbey National, it is now part of Santander UK.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Cake Entertainment</td>
<td style="text-align: left;">/wiki/Cake_Entertainment</td>
<td style="text-align: left;">Cake Entertainment</td>
<td style="text-align: left;">Cake Entertainment</td>
<td style="text-align: left;">Cake Entertainment — TV series production and distribution company. Established in 2002, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Cambridge Water Company</td>
<td style="text-align: left;">/wiki/Cambridge_Water_Company</td>
<td style="text-align: left;">Cambridge Water Company</td>
<td style="text-align: left;">Cambridge Water Company</td>
<td style="text-align: left;">Cambridge Water Company — utility company (water supply). Established in 1853, it is now part of South Staffordshire Water.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Camelot Group</td>
<td style="text-align: left;">/wiki/Camelot_Group</td>
<td style="text-align: left;">Camelot Group</td>
<td style="text-align: left;">Camelot Group</td>
<td style="text-align: left;">Camelot Group — lottery company. Established in 1998, its headquarters is in Watford.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Caparo Vehicle Technologies</td>
<td style="text-align: left;">/wiki/Caparo_Vehicle_Technologies</td>
<td style="text-align: left;">Caparo Vehicle Technologies</td>
<td style="text-align: left;">Caparo Vehicle Technologies</td>
<td style="text-align: left;">Caparo Vehicle Technologies — automotive and aerospace design and engineering and sports car production company. It was established in 2006.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Capitol Films</td>
<td style="text-align: left;">/wiki/Capitol_Films</td>
<td style="text-align: left;">Capitol Films</td>
<td style="text-align: left;">Capitol Films</td>
<td style="text-align: left;">Capitol Films — film production and distribution company, 1989–2013.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Carnival Corporation &amp; plc</td>
<td style="text-align: left;">/wiki/Carnival_Corporation_%26_plc</td>
<td style="text-align: left;">Carnival Corporation &amp; plc</td>
<td style="text-align: left;">Carnival Corporation &amp; plc</td>
<td style="text-align: left;">Carnival Corporation &amp; plc — British and American hospitality and tourism corporation (cruise operator with 10 cruise brands). It is composed of two companies – the US headquartered Carnival Corporation which is listed on the New York Stock Exchange, and the UK based Carnival plc which is listed on the UK Stock Exchange. Established in 1972, its headquarters are in Doral, Florida, US and Southampton, Hampshire UK. It was previously known as Carnival Cruise Line (which became a subsidiary), Carnival Corporation, and P&amp;O Princess Cruises. Its cruise lines are: Carnival Cruise Line, Cunard Line, P&amp;O Cruises, Holland America Line, Princess Cruises, Seabourn Cruise Line, P&amp;O Cruises Australia, Carnival Cruise Line Australia, CSSC Carnival Cruise Shipping, Costa Cruises, and AIDA Cruises. Former brands are: A’Rosa Cruises, Fathom, Fiesta Marina Cruises, Ibero Cruises, Ocean Village, Swan Hellenic, and Windstar Cruises. In 2019 its revenue was $20.83 billion, with net income of $2.99 billion.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Cartoon Network Studios Europe</td>
<td style="text-align: left;">/wiki/Cartoon_Network_Studios_Europe</td>
<td style="text-align: left;">Cartoon Network Studios Europe</td>
<td style="text-align: left;">Cartoon Network Studios Europe</td>
<td style="text-align: left;">Cartoon Network Studios Europe animation studio. Established in 2007, its headquarters is in London. It is also known as Great Marlborough Productions, and formerly as Cartoon Network Development Studio Europe.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Cater Allen</td>
<td style="text-align: left;">/wiki/Cater_Allen</td>
<td style="text-align: left;">Cater Allen</td>
<td style="text-align: left;">Cater Allen</td>
<td style="text-align: left;">Cater Allen — financial services company (private banking). Established in 1816, its headquarters is in London. Its parent company is Santander Group.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Caterham Cars</td>
<td style="text-align: left;">/wiki/Caterham_Cars</td>
<td style="text-align: left;">Caterham Cars</td>
<td style="text-align: left;">Caterham Cars</td>
<td style="text-align: left;">Caterham Cars — automobile manufacturing company (sports cars, F1). Established in 1973 at Caterham, Surrey, its headquarters is in Crawley, Sussex. It has also traded as Seven Cars Limited.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">SES Water</td>
<td style="text-align: left;">/wiki/SES_Water#East_Surrey_Water</td>
<td style="text-align: left;">Caterham Springwater Company</td>
<td style="text-align: left;">Caterham Springwater Company</td>
<td style="text-align: left;">Caterham Springwater Company — utility company (water supply), 1852–1885. In 1885 it was merged with Kenley Water Company to form the East Surrey Water Company.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Catford Studios</td>
<td style="text-align: left;">/wiki/Catford_Studios</td>
<td style="text-align: left;">Catford Studios</td>
<td style="text-align: left;">Catford Studios</td>
<td style="text-align: left;">Catford Studios film studio, 1914–1921. Located in Catford, London, it was also known as Windsor Studios.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Celltech</td>
<td style="text-align: left;">/wiki/Celltech</td>
<td style="text-align: left;">Celltech</td>
<td style="text-align: left;">Celltech</td>
<td style="text-align: left;">Celltech — biotechnology company, 1980–2004. Its headquarters was in Slough. In 1999 it was acquired by Chiroscience to briefly become Celltech Chiroscience. Celltech was acquired by UCB in 2004 to form UCB Celltech.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Central Electricity Generating Board</td>
<td style="text-align: left;">/wiki/Central_Electricity_Generating_Board</td>
<td style="text-align: left;">Central Electricity Generating Board</td>
<td style="text-align: left;">Central Electricity Generating Board</td>
<td style="text-align: left;">Central Electricity Generating Board — state owned electricity generation and transmission company, 1957–2001. Its headquarters was in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Centrica</td>
<td style="text-align: left;">/wiki/Centrica</td>
<td style="text-align: left;">Centrica</td>
<td style="text-align: left;">Centrica</td>
<td style="text-align: left;">Centrica — British multinational energy supplier (electric and gas), and services company. Established in 1997, its headquarters is in Windsor, Berkshire. It was formed when British Gas plc was split into Centrica, BG Group, and Transco. Its trading names include British Gas, Scottish Gas, Bord Gais Energy, and Direct Energy. In 2019 its revenue was £26.8 billion, with net income of £1.1 billion.</td>
</tr>
<tr class="even">
<td style="text-align: left;">AP Films</td>
<td style="text-align: left;">/wiki/AP_Films</td>
<td style="text-align: left;">AP Films</td>
<td style="text-align: left;">AP Films</td>
<td style="text-align: left;">Century 21 Productions - television and film production company. See AP Films.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Film4 Productions</td>
<td style="text-align: left;">/wiki/Film4_Productions</td>
<td style="text-align: left;">Film4 Productions</td>
<td style="text-align: left;">Film4 Productions</td>
<td style="text-align: left;">Channel Four Films — film production company. See Film4 Productions.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Arrival (company)</td>
<td style="text-align: left;">/wiki/Arrival_(company)</td>
<td style="text-align: left;">Arrival</td>
<td style="text-align: left;">Arrival</td>
<td style="text-align: left;">Charge Automotive — electric vehicle manufacturing company. See Arrival.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Charles Urban Trading Company</td>
<td style="text-align: left;">/wiki/Charles_Urban_Trading_Company</td>
<td style="text-align: left;">Charles Urban Trading Company</td>
<td style="text-align: left;">Charles Urban Trading Company</td>
<td style="text-align: left;">Charles Urban Trading Company — film production company, 1903–1914/18. Its headquarters was in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Charlotte Street Partners</td>
<td style="text-align: left;">/wiki/Charlotte_Street_Partners</td>
<td style="text-align: left;">Charlotte Street Partners</td>
<td style="text-align: left;">Charlotte Street Partners</td>
<td style="text-align: left;">Charlotte Street Partners — communications company. Established in 2014, its headquarters is in Edinburgh.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Chartered Bank of India, Australia and China</td>
<td style="text-align: left;">/wiki/Chartered_Bank_of_India,_Australia_and_China</td>
<td style="text-align: left;">Chartered Bank of India, Australia and China</td>
<td style="text-align: left;">Chartered Bank of India, Australia and China</td>
<td style="text-align: left;">Chartered Bank of India, Australia and China — multinational British banking company, 1853–1969. Its headquarters was in London. In 1969 it was merged with Standard Bank Limited to form Standard Chartered Bank.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Chelgate</td>
<td style="text-align: left;">/wiki/Chelgate</td>
<td style="text-align: left;">Chelgate</td>
<td style="text-align: left;">Chelgate</td>
<td style="text-align: left;">Chelgate — public relations and public affairs company. Established in 1988, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Chelsea Waterworks Company</td>
<td style="text-align: left;">/wiki/Chelsea_Waterworks_Company</td>
<td style="text-align: left;">Chelsea Waterworks Company</td>
<td style="text-align: left;">Chelsea Waterworks Company</td>
<td style="text-align: left;">Chelsea Waterworks Company — utility company (water), 1723–1902. Headquartered in London, it became part of the Metropolitan Water Board.</td>
</tr>
<tr class="even">
<td style="text-align: left;">SES Water</td>
<td style="text-align: left;">/wiki/SES_Water#East_Surrey_Water</td>
<td style="text-align: left;">Chelsham and Woldingham Water Company</td>
<td style="text-align: left;">Chelsham and Woldingham Water Company</td>
<td style="text-align: left;">Chelsham and Woldingham Water Company — utility company (water supply), 1884–1930. It became part of East Surrey Water Company.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Hafren Dyfrdwy</td>
<td style="text-align: left;">/wiki/Hafren_Dyfrdwy#History</td>
<td style="text-align: left;">Chester Waterworks Company</td>
<td style="text-align: left;">Chester Waterworks Company</td>
<td style="text-align: left;">Chester Waterworks Company — utility company (water supply), 1838–1997. Headquartered in Chester, it was formerly known as the City of Chester Waterworks Company. In 1997 it became part of Dee Valley Water.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Child &amp; Co.</td>
<td style="text-align: left;">/wiki/Child_%26_Co.</td>
<td style="text-align: left;">Child &amp; Co.</td>
<td style="text-align: left;">Child &amp; Co.</td>
<td style="text-align: left;">Child &amp; Co. — financial services company (private banking and wealth management). Formerly a Goldsmiths, it was established in 1664 and is the oldest bank in the U.K. Headquartered in London, it is a branch of the Royal Bank of Scotland.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Children’s Film Unit</td>
<td style="text-align: left;">/wiki/Children%27s_Film_Unit</td>
<td style="text-align: left;">Children’s Film Unit</td>
<td style="text-align: left;">Children’s Film Unit</td>
<td style="text-align: left;">Children’s Film Unit — film production company, 1981–2011.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Chime Communications Limited</td>
<td style="text-align: left;">/wiki/Chime_Communications_Limited</td>
<td style="text-align: left;">Chime Communications Limited</td>
<td style="text-align: left;">Chime Communications Limited</td>
<td style="text-align: left;">Chime Communications Limited — marketing services company. Established in 1989, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Chiroscience</td>
<td style="text-align: left;">/wiki/Chiroscience</td>
<td style="text-align: left;">Chiroscience</td>
<td style="text-align: left;">Chiroscience</td>
<td style="text-align: left;">Chiroscience — biotechnology company, 1991–1999. In 1996 it was merged with Darwin Molecular Corporation. In 1999 it was acquired by Celltech who, in 2004, was acquired by UCB.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Cholderton and District Water Company</td>
<td style="text-align: left;">/wiki/Cholderton_and_District_Water_Company</td>
<td style="text-align: left;">Cholderton and District Water Company</td>
<td style="text-align: left;">Cholderton and District Water Company</td>
<td style="text-align: left;">Cholderton and District Water Company — utility company (water supply). It was established in 1904.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Chorion (company)</td>
<td style="text-align: left;">/wiki/Chorion_(company)</td>
<td style="text-align: left;">Chorion</td>
<td style="text-align: left;">Chorion</td>
<td style="text-align: left;">Chorion — media, film and TV production and distribution company, 1998–2012.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Churchill Mining</td>
<td style="text-align: left;">/wiki/Churchill_Mining</td>
<td style="text-align: left;">Churchill Mining</td>
<td style="text-align: left;">Churchill Mining</td>
<td style="text-align: left;">Churchill Mining — coal mining company. Established in 2005, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Cineguild Productions</td>
<td style="text-align: left;">/wiki/Cineguild_Productions</td>
<td style="text-align: left;">Cineguild Productions</td>
<td style="text-align: left;">Cineguild Productions</td>
<td style="text-align: left;">Cineguild Productions — film production company, 1944–1951.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Cineworld</td>
<td style="text-align: left;">/wiki/Cineworld</td>
<td style="text-align: left;">Cineworld</td>
<td style="text-align: left;">Cineworld</td>
<td style="text-align: left;">Cineworld — cinema chain company. Established in 1995, its headquarters is in London. In 2019 its revenue was £4.3 billion, with net income of £180.3 million.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Cirkle</td>
<td style="text-align: left;">/wiki/Cirkle</td>
<td style="text-align: left;">Cirkle</td>
<td style="text-align: left;">Cirkle</td>
<td style="text-align: left;">Cirkle — public relations company. Established in 1986, its headquarters is in Beaconsfield.</td>
</tr>
<tr class="even">
<td style="text-align: left;">CiteAb</td>
<td style="text-align: left;">/wiki/CiteAb</td>
<td style="text-align: left;">CiteAb</td>
<td style="text-align: left;">CiteAb</td>
<td style="text-align: left;">CiteAb — biotechnology and life sciences data company (search engine for research antibodies). Established in 2014, its headquarters is in Bath, Somerset.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Clearwater Features</td>
<td style="text-align: left;">/wiki/Clearwater_Features</td>
<td style="text-align: left;">Clearwater Features</td>
<td style="text-align: left;">Clearwater Features</td>
<td style="text-align: left;">Clearwater Features — film and TV production company, 1979–1990. Its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Clerical Medical</td>
<td style="text-align: left;">/wiki/Clerical_Medical</td>
<td style="text-align: left;">Clerical Medical</td>
<td style="text-align: left;">Clerical Medical</td>
<td style="text-align: left;">Clerical Medical — financial services company (life insurance, pensions, and investment). Established in 1824, its headquarters is in London. It was formerly known as the Medical, Clerical and General Life Assurance Society. Its parent company is Lloyds Banking Group.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Clifton and Kersley Coal Company</td>
<td style="text-align: left;">/wiki/Clifton_and_Kersley_Coal_Company</td>
<td style="text-align: left;">Clifton and Kersley Coal Company</td>
<td style="text-align: left;">Clifton and Kersley Coal Company</td>
<td style="text-align: left;">Clifton and Kersley Coal Company — coal mining company, 1861–1929. It became part of Manchester Collieries.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Cloud Eight Films</td>
<td style="text-align: left;">/wiki/Cloud_Eight_Films</td>
<td style="text-align: left;">Cloud Eight Films</td>
<td style="text-align: left;">Cloud Eight Films</td>
<td style="text-align: left;">Cloud Eight Films — film and television production company. Established in 2009, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Coalite</td>
<td style="text-align: left;">/wiki/Coalite</td>
<td style="text-align: left;">Coalite Company</td>
<td style="text-align: left;">Coalite Company</td>
<td style="text-align: left;">Coalite Company — coke, petrol, and oils production company, 1917–2004. Established in London, its headquarters was in Bolsover. It was also known as The Coalite Chemicals Company.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Codex Pictures</td>
<td style="text-align: left;">/wiki/Codex_Pictures</td>
<td style="text-align: left;">Codex Pictures</td>
<td style="text-align: left;">Codex Pictures</td>
<td style="text-align: left;">Codex Pictures — film production company, 2008–2013. Its headquarters was in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Colne Valley Water</td>
<td style="text-align: left;">/wiki/Colne_Valley_Water</td>
<td style="text-align: left;">Colne Valley Water</td>
<td style="text-align: left;">Colne Valley Water</td>
<td style="text-align: left;">Colne Valley Water — utility company (water supply), 1873–1994. In 1994 it was merged into Three Valleys Water.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Tanfield Group</td>
<td style="text-align: left;">/wiki/Tanfield_Group</td>
<td style="text-align: left;">Tanfield Group</td>
<td style="text-align: left;">Tanfield Group</td>
<td style="text-align: left;">Comeleon - automotive, and mobile phone technology company. See Tanfield Group.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Company of Mineral and Battery Works</td>
<td style="text-align: left;">/wiki/Company_of_Mineral_and_Battery_Works</td>
<td style="text-align: left;">Company of Mineral and Battery Works</td>
<td style="text-align: left;">Company of Mineral and Battery Works</td>
<td style="text-align: left;">Company of Mineral and Battery Works — metal, mining, and wire works company, 1565–c1750.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Compass Group</td>
<td style="text-align: left;">/wiki/Compass_Group</td>
<td style="text-align: left;">Compass Group</td>
<td style="text-align: left;">Compass Group</td>
<td style="text-align: left;">Compass Group — British multinational contract food service, cleaning, and facilities management company. Established in 1941, its headquarters is in Chertsey. It was formerly known as Factory Canteens Limited, and Bateman Catering. In 2019 its revenue was £24.8 billion, with a net income of £1.1 billion.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Framestore</td>
<td style="text-align: left;">/wiki/Framestore</td>
<td style="text-align: left;">Computer Film Company</td>
<td style="text-align: left;">Computer Film Company</td>
<td style="text-align: left;">Computer Film Company — film visual effects company. Established in 1986, its headquarters is in London. It was merged with Framestore.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Consolidated Gold Fields</td>
<td style="text-align: left;">/wiki/Consolidated_Gold_Fields</td>
<td style="text-align: left;">Consolidated Gold Fields</td>
<td style="text-align: left;">Consolidated Gold Fields</td>
<td style="text-align: left;">Consolidated Gold Fields — gold mining company, 1887–1988. Headquartered in London, it was acquired by Hanson.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">ConvaTec</td>
<td style="text-align: left;">/wiki/ConvaTec</td>
<td style="text-align: left;">ConvaTec</td>
<td style="text-align: left;">ConvaTec</td>
<td style="text-align: left;">ConvaTec — medical devices company. Established in 1978, its headquarters is in Reading, Berkshire. It was formerly a division of E.R. Squibb &amp; Sons, Inc.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Co-op Energy</td>
<td style="text-align: left;">/wiki/Co-op_Energy</td>
<td style="text-align: left;">Co-op Energy</td>
<td style="text-align: left;">Co-op Energy</td>
<td style="text-align: left;">Co-op Energy — energy company (electricity supplier). Established in 2010, its headquarters is in Warwick. Its parent company is The Midcounties Co-operative.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">The Co-operative Bank</td>
<td style="text-align: left;">/wiki/The_Co-operative_Bank</td>
<td style="text-align: left;">The Co-operative Bank plc</td>
<td style="text-align: left;">The Co-operative Bank plc</td>
<td style="text-align: left;">The Co-operative Bank plc — financial services company (banking). Established in 1872, its headquarters is in Manchester. It was first formed as the Loan and Deposit Department of the Co-operative Wholesale Society. In 2009, it merged with the Britannia Building Society. In 2018, it had an operating income of £369 million. Its parent company is The Co-operative Bank Holdings Ltd.</td>
</tr>
<tr class="even">
<td style="text-align: left;">The Co-operative Banking Group</td>
<td style="text-align: left;">/wiki/The_Co-operative_Banking_Group</td>
<td style="text-align: left;">The Co-operative Banking Group</td>
<td style="text-align: left;">The Co-operative Banking Group</td>
<td style="text-align: left;">The Co-operative Banking Group — financial services company (banking and insurance), 2002–2013. Its headquarters was in Manchester. Formerly known as Co-operative Financial Services, its subsidiaries were The Co-operative Bank and Co-op Insurance Services Ltd. Its parent company was The Co-operative Group.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Co-operative Federal Trading Services</td>
<td style="text-align: left;">/wiki/Co-operative_Federal_Trading_Services</td>
<td style="text-align: left;">Co-operative Federal Trading Services</td>
<td style="text-align: left;">Co-operative Federal Trading Services</td>
<td style="text-align: left;">Co-operative Federal Trading Services — co-operative federation (groceries wholesaler). Established in 2015, its headquarters is One Angel Square, Manchester. It is managed by The Co-operative Group.</td>
</tr>
<tr class="even">
<td style="text-align: left;">The Co-operative Group</td>
<td style="text-align: left;">/wiki/The_Co-operative_Group</td>
<td style="text-align: left;">The Co-operative Group</td>
<td style="text-align: left;">The Co-operative Group</td>
<td style="text-align: left;">The Co-operative Group (Co-op) — consumers’ co-operative (food retail and wholesale, e-pharmacy, insurance services, legal services, funeral care, land and property management). Established in 1844, its headquarters is One Angel Square, Manchester. First established as the Rochdale Society of Equitable Pioneers, in 1872 it became The Co-operative Wholesale Society. Its 2017 revenue was £9.5 billion, with a net income of £72 million.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Co-op Insurance</td>
<td style="text-align: left;">/wiki/Co-op_Insurance</td>
<td style="text-align: left;">Co-op Insurance Services Ltd</td>
<td style="text-align: left;">Co-op Insurance Services Ltd</td>
<td style="text-align: left;">Co-op Insurance Services Ltd — insurance services company (general insurance; formerly also life insurance, and fund management). Established in 1867, its headquarters is at CIS Tower, Manchester. Its parent company is The Co-operative Group.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Co-op Legal Services</td>
<td style="text-align: left;">/wiki/Co-op_Legal_Services</td>
<td style="text-align: left;">Co-op Legal Services</td>
<td style="text-align: left;">Co-op Legal Services</td>
<td style="text-align: left;">Co-op Legal Services — legal services company. Established in 2006, its headquarters is in Manchester. Its parent company is The Co-operative Group.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Co-operative Federal Trading Services</td>
<td style="text-align: left;">/wiki/Co-operative_Federal_Trading_Services#Co-operative_Retail_Trading_Group_1993-2015</td>
<td style="text-align: left;">Co-operative Retail Trading Group</td>
<td style="text-align: left;">Co-operative Retail Trading Group</td>
<td style="text-align: left;">Co-operative Retail Trading Group — co-operative federation (groceries wholesaler), 1993–2015. Headquartered in Manchester, it was managed by The Co-operative Group.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Cooper Car Company</td>
<td style="text-align: left;">/wiki/Cooper_Car_Company</td>
<td style="text-align: left;">Cooper Car Company</td>
<td style="text-align: left;">Cooper Car Company</td>
<td style="text-align: left;">Cooper Car Company — automobile manufacturing company (racing cars, and sports cars). Established in 1947, its headquarters is in Surbiton, Surrey.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Bigballs Media</td>
<td style="text-align: left;">/wiki/Bigballs_Media</td>
<td style="text-align: left;">Bigballs Media</td>
<td style="text-align: left;">Bigballs Media</td>
<td style="text-align: left;">Copa90 — football media company. See Bigballs Media.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Coral (bookmaker)</td>
<td style="text-align: left;">/wiki/Coral_(bookmaker)</td>
<td style="text-align: left;">Coral</td>
<td style="text-align: left;">Coral</td>
<td style="text-align: left;">Coral — gambling company. Established in 1926, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Corbyn, Stacey &amp; Company</td>
<td style="text-align: left;">/wiki/Corbyn,<em>Stacey</em>%26_Company</td>
<td style="text-align: left;">Corbyn, Stacey &amp; Company</td>
<td style="text-align: left;">Corbyn, Stacey &amp; Company</td>
<td style="text-align: left;">Corbyn, Stacey &amp; Company — pharmaceuticals, and retail chemists company, 1726–1927. It was headquartered in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Costa Coffee</td>
<td style="text-align: left;">/wiki/Costa_Coffee</td>
<td style="text-align: left;">Costa Coffee</td>
<td style="text-align: left;">Costa Coffee</td>
<td style="text-align: left;">Costa Coffee — British multinational coffee-house company. Established in 1971 in London, its headquarters is in Dunstable. It was acquired by Whitbread in 1995, then by Coca-Cola in 2019.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Coutts</td>
<td style="text-align: left;">/wiki/Coutts</td>
<td style="text-align: left;">Coutts &amp; Company</td>
<td style="text-align: left;">Coutts &amp; Company</td>
<td style="text-align: left;">Coutts &amp; Company — financial services company (private banking and wealth management). Established in 1692, its headquarters is in London. Its parent company is NatWest Holdings which is owned by the NatWest Group. In 2018 its revenue was £681 million, with a net income of £268 million.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Cove Energy plc</td>
<td style="text-align: left;">/wiki/Cove_Energy_plc</td>
<td style="text-align: left;">Cove Energy plc</td>
<td style="text-align: left;">Cove Energy plc</td>
<td style="text-align: left;">Cove Energy plc — oil and gas exploration company (assets in East Africa), 2009–2012.Its headquarters is in London. In 2012 it was acquired by PTT Exploration and Production.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Cow &amp; Gate</td>
<td style="text-align: left;">/wiki/Cow_%26_Gate</td>
<td style="text-align: left;">Cow &amp; Gate</td>
<td style="text-align: left;">Cow &amp; Gate</td>
<td style="text-align: left;">Cow &amp; Gate — dairy products, and babyfood company. Established in 1882, its headquarters is in Guildford, Surrey. It was formerly known as West Surrey Dairy, and West Surrey Central Dairy Company Limited. In 1959 it merged with United Dairies to form Unigate.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Cricklewood Studios</td>
<td style="text-align: left;">/wiki/Cricklewood_Studios</td>
<td style="text-align: left;">Cricklewood Studios</td>
<td style="text-align: left;">Cricklewood Studios</td>
<td style="text-align: left;">Cricklewood Studios — film studios, 1920–1938. Located in London, it was also known as Stoll Film Studios.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Croda International</td>
<td style="text-align: left;">/wiki/Croda_International</td>
<td style="text-align: left;">Croda International plc</td>
<td style="text-align: left;">Croda International plc</td>
<td style="text-align: left;">Croda International plc — chemicals company (consumer and industrial products). Established in 1925, its headquarters is in Snaith, East Riding of Yorkshire. In 2019 its revenue was £1.37 billion, with a net income of £223 million.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Crookes Healthcare</td>
<td style="text-align: left;">/wiki/Crookes_Healthcare</td>
<td style="text-align: left;">Crookes Healthcare</td>
<td style="text-align: left;">Crookes Healthcare</td>
<td style="text-align: left;">Crookes Healthcare — healthcare products and pharmaceuticals company. Established in 1918 in London, its headquarters is in Lenton, Nottingham. It was formerly known as Crookes Collosols, and The Crookes Laboratories. In 1960 it was acquired by Arthur Guinness Son and Company, then in 1971 it was acquired by Boots, and, in 2006, it was acquired by Reckitt Benckiser.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Crosslé Car Company</td>
<td style="text-align: left;">/wiki/Crossl%C3%A9_Car_Company</td>
<td style="text-align: left;">Crosslé Car Company</td>
<td style="text-align: left;">Crosslé Car Company</td>
<td style="text-align: left;">Crosslé Car Company — racing car manufacturing company. Established in 1957, its headquarters is in Holywood, Northern Ireland.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Crown Film Unit</td>
<td style="text-align: left;">/wiki/Crown_Film_Unit</td>
<td style="text-align: left;">Crown Film Unit</td>
<td style="text-align: left;">Crown Film Unit</td>
<td style="text-align: left;">Crown Film Unit — film production company, 1940–1952. It was formerly the GPO Film Unit.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Curzon Cinemas</td>
<td style="text-align: left;">/wiki/Curzon_Cinemas</td>
<td style="text-align: left;">Curzon Cinemas</td>
<td style="text-align: left;">Curzon Cinemas</td>
<td style="text-align: left;">Curzon Cinemas — cinema chain company. It was established in 1934.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Davrian</td>
<td style="text-align: left;">/wiki/Davrian</td>
<td style="text-align: left;">Davrian Developments</td>
<td style="text-align: left;">Davrian Developments</td>
<td style="text-align: left;">Davrian Developments — automobile manufacturing company, 1967–1983. It was headquartered in Clapham, London, then Tregaron, Wales, and then Lampeter, Wales.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Derwent Valley Water Board</td>
<td style="text-align: left;">/wiki/Derwent_Valley_Water_Board</td>
<td style="text-align: left;">Derwent Valley Water Board</td>
<td style="text-align: left;">Derwent Valley Water Board</td>
<td style="text-align: left;">Derwent Valley Water Board — state owned utility company (water), 1899–1974. It was succeeded by Severn Trent Water Authority.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Diageo</td>
<td style="text-align: left;">/wiki/Diageo</td>
<td style="text-align: left;">Diageo plc</td>
<td style="text-align: left;">Diageo plc</td>
<td style="text-align: left;">Diageo plc — British multinational alcoholic beverages company. Established in 1997, its headquarters is in Park Royal, London. Its brands include Smirnoff, Johnnie Walker, Baileys, and Guinness). It was formed from the merger of Guinness Brewery and Grand Metropolitan. In 2019 its revenue was £12.8 billion, with a net income of £3.3 billion.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Dial-a-Phone</td>
<td style="text-align: left;">/wiki/Dial-a-Phone</td>
<td style="text-align: left;">Dial-a-Phone</td>
<td style="text-align: left;">Dial-a-Phone</td>
<td style="text-align: left;">Dial-a-Phone — mobile phone retail company, 1995–2014. Its headquarters was in Newcastle-under-Lyme, Staffordshire.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Digital Cybercherries</td>
<td style="text-align: left;">/wiki/Digital_Cybercherries</td>
<td style="text-align: left;">Digital Cybercherries Ltd</td>
<td style="text-align: left;">Digital Cybercherries Ltd</td>
<td style="text-align: left;">Digital Cybercherries Ltd — video games company (games developer). It was established in 2015.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">The Distillers Company</td>
<td style="text-align: left;">/wiki/The_Distillers_Company</td>
<td style="text-align: left;">The Distillers Company</td>
<td style="text-align: left;">The Distillers Company</td>
<td style="text-align: left;">The Distillers Company — Scottish whiskey, pharmaceuticals, chemicals and plastics company, 1877–1986. Headquartered in Edinburgh, Scotland, it was acquired by Guinness in 1986 to form United Distillers.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Dixons Carphone</td>
<td style="text-align: left;">/wiki/Dixons_Carphone</td>
<td style="text-align: left;">Dixons Carphone</td>
<td style="text-align: left;">Dixons Carphone</td>
<td style="text-align: left;">Dixons Carphone — British multinational electrical and telecommunications retail and services company. It was established in 2014 by the merger of Dixons Retail and Carphone Warehouse Group. Its headquarters was in London. In 2019 its revenue wes £10.4 billion, with net income of £320 million.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">DNA Bioscience</td>
<td style="text-align: left;">/wiki/DNA_Bioscience</td>
<td style="text-align: left;">DNA Bioscience</td>
<td style="text-align: left;">DNA Bioscience</td>
<td style="text-align: left;">DNA Bioscience — biotechnology company (DNA paternity testing), 2003–2005.</td>
</tr>
<tr class="even">
<td style="text-align: left;">DNA Films</td>
<td style="text-align: left;">/wiki/DNA_Films</td>
<td style="text-align: left;">DNA Films</td>
<td style="text-align: left;">DNA Films</td>
<td style="text-align: left;">DNA Films — film production company. Its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">DNEG</td>
<td style="text-align: left;">/wiki/DNEG</td>
<td style="text-align: left;">DNEG</td>
<td style="text-align: left;">DNEG</td>
<td style="text-align: left;">DNEG — film visual effects, animation, and stereo conversion company. Established in 1998, its headquarters is in London. It was formerly known as Double Negative.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Dolomite Bio</td>
<td style="text-align: left;">/wiki/Dolomite_Bio</td>
<td style="text-align: left;">Dolomite Bio</td>
<td style="text-align: left;">Dolomite Bio</td>
<td style="text-align: left;">Dolomite Bio — biotechnology company (single cell sequencing). Established in 2016, its headquarters is in Royston, Hertfordshire. It is part of Blacktrace Holdings Ltd.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">SES Water</td>
<td style="text-align: left;">/wiki/SES_Water#East_Surrey_Water</td>
<td style="text-align: left;">Dorking Water Company</td>
<td style="text-align: left;">Dorking Water Company</td>
<td style="text-align: left;">Dorking Water Company — utility company (water supply), 1869–1959. Headquartered in Dorking, Surrey, it became part of East Surrey Water Company.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Douglas Equipment</td>
<td style="text-align: left;">/wiki/Douglas_Equipment</td>
<td style="text-align: left;">Douglas Equipment</td>
<td style="text-align: left;">Douglas Equipment</td>
<td style="text-align: left;">Douglas Equipment — support vehicles manufacturing company (for airports, aircraft, and docks). Established in 1947, its headquarters was in Cheltenham. It was formerly known as FL Douglas. It was later purchased by Textron.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Dragon International Film Studios</td>
<td style="text-align: left;">/wiki/Dragon_International_Film_Studios</td>
<td style="text-align: left;">Dragon International Film Studios</td>
<td style="text-align: left;">Dragon International Film Studios</td>
<td style="text-align: left;">Dragon International Film Studios — film and TV studios. Established in 2006, it is located in Llanilid, Wales.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Rogue Films</td>
<td style="text-align: left;">/wiki/Rogue_Films</td>
<td style="text-align: left;">Rogue Films</td>
<td style="text-align: left;">Rogue Films</td>
<td style="text-align: left;">Drum Films — film and TV production company. See Rogue Films.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Drummonds Bank</td>
<td style="text-align: left;">/wiki/Drummonds_Bank</td>
<td style="text-align: left;">Drummonds Bank</td>
<td style="text-align: left;">Drummonds Bank</td>
<td style="text-align: left;">Drummonds Bank — financial services company (private banking and wealth management). Established in 1717, its headquarters is in London. It is a branch of the Royal Bank of Scotland.</td>
</tr>
<tr class="even">
<td style="text-align: left;">DS Smith</td>
<td style="text-align: left;">/wiki/DS_Smith</td>
<td style="text-align: left;">DS Smith plc</td>
<td style="text-align: left;">DS Smith plc</td>
<td style="text-align: left;">DS Smith plc — international packaging company (corrugated packaging, plastic packaging, and recycled paper). Established in 1940, its headquarters is in London. In 2019 its revenue was £6.1 billion, with net income of £274 million.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Eagle-Lion Films</td>
<td style="text-align: left;">/wiki/Eagle-Lion_Films</td>
<td style="text-align: left;">Eagle-Lion Films</td>
<td style="text-align: left;">Eagle-Lion Films</td>
<td style="text-align: left;">Eagle-Lion Films — film production and distribution company, 1946–1950.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Ealing Studios</td>
<td style="text-align: left;">/wiki/Ealing_Studios</td>
<td style="text-align: left;">Ealing Studios</td>
<td style="text-align: left;">Ealing Studios</td>
<td style="text-align: left;">Ealing Studios — film and television production, and studios company. Established in 1902 in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">East London Waterworks Company</td>
<td style="text-align: left;">/wiki/East_London_Waterworks_Company</td>
<td style="text-align: left;">East London Waterworks Company</td>
<td style="text-align: left;">East London Waterworks Company</td>
<td style="text-align: left;">East London Waterworks Company — utility company (water), 1806–1904. Headquartered in London, it became part of the Metropolitan Water Board.</td>
</tr>
<tr class="even">
<td style="text-align: left;">SES Water</td>
<td style="text-align: left;">/wiki/SES_Water#East_Surrey_Water</td>
<td style="text-align: left;">East Surrey Water Company</td>
<td style="text-align: left;">East Surrey Water Company</td>
<td style="text-align: left;">East Surrey Water Company — utility company (water supply), 1885–1996. It was formed by the merger of Caterham Springwater Company with Kenley Water Company. In 1996 it was merged with Sutton District Water to become Sutton and East Surrey Water.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Eastern Electricity</td>
<td style="text-align: left;">/wiki/Eastern_Electricity</td>
<td style="text-align: left;">Eastern Electricity</td>
<td style="text-align: left;">Eastern Electricity</td>
<td style="text-align: left;">Eastern Electricity — energy company (electricity supply and distribution), 1948–1995. Headquartered in London, it was also known as Eastern Group. In 1995 it was acquired by Hanson plc.</td>
</tr>
<tr class="even">
<td style="text-align: left;">EasyGroup</td>
<td style="text-align: left;">/wiki/EasyGroup</td>
<td style="text-align: left;">EasyGroup Holdings</td>
<td style="text-align: left;">EasyGroup Holdings</td>
<td style="text-align: left;">EasyGroup Holdings — brand licensing company. Established in 1998, its headquarters is in Kensington, London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">EasyJet</td>
<td style="text-align: left;">/wiki/EasyJet</td>
<td style="text-align: left;">EasyJet plc</td>
<td style="text-align: left;">EasyJet plc</td>
<td style="text-align: left;">EasyJet plc — airline group company (comprising EasyJet UK, EasyJet Switzerland and EasyJet Europe). Established in 1995, its headquarters is at London Luton Airport, Luton, Bedfordshire. Its 2019 revenue was £6.3 billion, with net income of £349 million.</td>
</tr>
<tr class="even">
<td style="text-align: left;">EasyJet UK</td>
<td style="text-align: left;">/wiki/EasyJet_UK</td>
<td style="text-align: left;">EasyJet UK</td>
<td style="text-align: left;">EasyJet UK</td>
<td style="text-align: left;">EasyJet UK — airline company. Established in 2017, its headquarters is at London Luton Airport, Luton, Bedfordshire. Its parent company is Easy Jet plc.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Ecosse Films</td>
<td style="text-align: left;">/wiki/Ecosse_Films</td>
<td style="text-align: left;">Ecosse Films</td>
<td style="text-align: left;">Ecosse Films</td>
<td style="text-align: left;">Ecosse Films - film and television production company, headquartered in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Electricity North West</td>
<td style="text-align: left;">/wiki/Electricity_North_West</td>
<td style="text-align: left;">Electricity North West</td>
<td style="text-align: left;">Electricity North West</td>
<td style="text-align: left;">Electricity North West — energy company (electricity distribution). Established in 2007, its headquarters is in Warrington. It was formerly known as NORWEB. Its parent company is North West Electricity Networks.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Elstree Studios (Shenley Road)</td>
<td style="text-align: left;">/wiki/Elstree_Studios_(Shenley_Road)</td>
<td style="text-align: left;">Elstree Film Studios Ltd</td>
<td style="text-align: left;">Elstree Film Studios Ltd</td>
<td style="text-align: left;">Elstree Film Studios Ltd — film and TV production company. Established in 1925 it is located at Borehamwood.</td>
</tr>
<tr class="even">
<td style="text-align: left;">EMI Films</td>
<td style="text-align: left;">/wiki/EMI_Films</td>
<td style="text-align: left;">EMI Films</td>
<td style="text-align: left;">EMI Films</td>
<td style="text-align: left;">EMI Films — film production and distribution company, 1969–1986. It also operated under the names: EMI-Elstree, MGM-EMI, EMI Film Distributors Ltd, Anglo-EMI Film Distributors Ltd, Thorn EMI Screen Entertainment, and Thorn EMI.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Empire Cinemas</td>
<td style="text-align: left;">/wiki/Empire_Cinemas</td>
<td style="text-align: left;">Empire Cinemas Limited</td>
<td style="text-align: left;">Empire Cinemas Limited</td>
<td style="text-align: left;">Empire Cinemas Limited — cinema chain company, established in 2005.</td>
</tr>
<tr class="even">
<td style="text-align: left;">The Energy Group</td>
<td style="text-align: left;">/wiki/The_Energy_Group</td>
<td style="text-align: left;">The Energy Group</td>
<td style="text-align: left;">The Energy Group</td>
<td style="text-align: left;">The Energy Group — energy company (power generator and distributor), 1990–1998. Headquartered in London, it was acquired by Texas Utilities.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">English China Clays</td>
<td style="text-align: left;">/wiki/English_China_Clays</td>
<td style="text-align: left;">English China Clays</td>
<td style="text-align: left;">English China Clays</td>
<td style="text-align: left;">English China Clays — mining (china clay), stone quarries, building, and housing development company, 1919–1999. Headquartered in St Austell, Cornwall, it was acquired by Imetal.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Enlightenment Productions</td>
<td style="text-align: left;">/wiki/Enlightenment_Productions</td>
<td style="text-align: left;">Enlightenment Productions</td>
<td style="text-align: left;">Enlightenment Productions</td>
<td style="text-align: left;">Enlightenment Productions — film production and distribution company, headquartered in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Eon Productions</td>
<td style="text-align: left;">/wiki/Eon_Productions</td>
<td style="text-align: left;">Eon Productions</td>
<td style="text-align: left;">Eon Productions</td>
<td style="text-align: left;">Eon Productions — film production company. Established in 1961, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Eros Films</td>
<td style="text-align: left;">/wiki/Eros_Films</td>
<td style="text-align: left;">Eros Films</td>
<td style="text-align: left;">Eros Films</td>
<td style="text-align: left;">Eros Films — film production and distribution company, 1947–1961. Its headquarters was in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Essex and Suffolk Water</td>
<td style="text-align: left;">/wiki/Essex_and_Suffolk_Water</td>
<td style="text-align: left;">Essex and Suffolk Water</td>
<td style="text-align: left;">Essex and Suffolk Water</td>
<td style="text-align: left;">Essex and Suffolk Water — utility company (water supply). Established in 1994, it was formed from the merger of Essex Water Company and Suffolk Water Company. Since 2000 it is part of Northumbrian Water.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Everyman Cinemas</td>
<td style="text-align: left;">/wiki/Everyman_Cinemas</td>
<td style="text-align: left;">Everyman Cinemas</td>
<td style="text-align: left;">Everyman Cinemas</td>
<td style="text-align: left;">Everyman Cinemas — cinema chain company. Established in 1933, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Evraz</td>
<td style="text-align: left;">/wiki/Evraz</td>
<td style="text-align: left;">Evraz</td>
<td style="text-align: left;">Evraz</td>
<td style="text-align: left;">Evraz — steel, and mining company. Established in 1992 in Moscow, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Extra Energy</td>
<td style="text-align: left;">/wiki/Extra_Energy</td>
<td style="text-align: left;">Extra Energy</td>
<td style="text-align: left;">Extra Energy</td>
<td style="text-align: left;">Extra Energy — utility company (gas and electricity), 2014–2018. Its headquarters was in Birmingham.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Arash Motor Company</td>
<td style="text-align: left;">/wiki/Arash_Motor_Company</td>
<td style="text-align: left;">Arash Motor Company</td>
<td style="text-align: left;">Arash Motor Company</td>
<td style="text-align: left;">Farboud Limited — automobile manufacturing company. See Arash Motor Company.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Farmcare</td>
<td style="text-align: left;">/wiki/Farmcare</td>
<td style="text-align: left;">Farmcare Trading Ltd</td>
<td style="text-align: left;">Farmcare Trading Ltd</td>
<td style="text-align: left;">Farmcare Trading Ltd — farming and wholesale company. Established in 1896, it was formerly part of the Co-operative Wholesale Society, and then The Co-operative Group. It was also known as The Co-operative Farms. In 2014 it was sold to the Wellcome Trust.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Ferguson plc</td>
<td style="text-align: left;">/wiki/Ferguson_plc</td>
<td style="text-align: left;">Ferguson plc</td>
<td style="text-align: left;">Ferguson plc</td>
<td style="text-align: left;">Ferguson plc — building materials company (plumbing and heating products distributor). It was previously also a manufacturer of plumbing and heating products, and originally was a manufacturer of sheep shearing equipment. Established in 1887, its headquarters is in Winnersh Triangle. It was formerly known as Wolseley plc. In 2019 its revenue was $22 billion, with net income of $1.1 billion.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fifth Column Films</td>
<td style="text-align: left;">/wiki/Fifth_Column_Films</td>
<td style="text-align: left;">Fifth Column Films</td>
<td style="text-align: left;">Fifth Column Films</td>
<td style="text-align: left;">Fifth Column Films — film production company, established in 2006.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Film and Music Entertainment</td>
<td style="text-align: left;">/wiki/Film_and_Music_Entertainment</td>
<td style="text-align: left;">Film and Music Entertainment</td>
<td style="text-align: left;">Film and Music Entertainment</td>
<td style="text-align: left;">Film and Music Entertainment — film production company. Established in 2000, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Film Producers Guild</td>
<td style="text-align: left;">/wiki/Film_Producers_Guild</td>
<td style="text-align: left;">Film Producers Guild</td>
<td style="text-align: left;">Film Producers Guild</td>
<td style="text-align: left;">Film Producers Guild — documentary film production and distribution company. Established in 1944, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Film Tank</td>
<td style="text-align: left;">/wiki/Film_Tank</td>
<td style="text-align: left;">Film Tank</td>
<td style="text-align: left;">Film Tank</td>
<td style="text-align: left;">Film Tank — film production company. Established in 2009, its headquarters is in Burnham-on-Sea.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Film4 Productions</td>
<td style="text-align: left;">/wiki/Film4_Productions</td>
<td style="text-align: left;">Film4 Productions</td>
<td style="text-align: left;">Film4 Productions</td>
<td style="text-align: left;">Film4 Productions — film production company. Its previous names were: Channel Four Films, FilmFour International, and FilmFour.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fine Arts Films</td>
<td style="text-align: left;">/wiki/Fine_Arts_Films</td>
<td style="text-align: left;">Fine Arts Films</td>
<td style="text-align: left;">Fine Arts Films</td>
<td style="text-align: left;">Fine Arts Films — film and TV production company, established in 1955.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fingercuff Productions</td>
<td style="text-align: left;">/wiki/Fingercuff_Productions</td>
<td style="text-align: left;">Fingercuff Productions</td>
<td style="text-align: left;">Fingercuff Productions</td>
<td style="text-align: left;">Fingercuff Productions — film production company. Established in 2000, it is defunct.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Finsbury (public relations)</td>
<td style="text-align: left;">/wiki/Finsbury_(public_relations)</td>
<td style="text-align: left;">Finsbury</td>
<td style="text-align: left;">Finsbury</td>
<td style="text-align: left;">Finsbury — public relations company. Established in 1994, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Firmus Energy</td>
<td style="text-align: left;">/wiki/Firmus_Energy</td>
<td style="text-align: left;">Firmus Energy</td>
<td style="text-align: left;">Firmus Energy</td>
<td style="text-align: left;">Firmus Energy — energy company (gas and electricity). Established circa 2005, its headquarters is in Antrim, Northern Ireland. It was formerly a subsidiary of Bord Gáis. In 2019 it was acquired by Equitix.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">First Choice (UK)</td>
<td style="text-align: left;">/wiki/First_Choice_(UK)</td>
<td style="text-align: left;">First Choice Holidays Limited</td>
<td style="text-align: left;">First Choice Holidays Limited</td>
<td style="text-align: left;">First Choice Holidays Limited — travel company (travel agency, tour operator, airlines, hotels, cruise ships). Established in 1973, its headquarters is in Luton, Bedfordshire. It was formerly known as Owners Abroad. Its parent company is TUI AG.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Fisons</td>
<td style="text-align: left;">/wiki/Fisons</td>
<td style="text-align: left;">Fisons</td>
<td style="text-align: left;">Fisons</td>
<td style="text-align: left;">Fisons — British multinational pharmaceuticals, scientific instruments, and horticultural chemicals company, 1843–1995. Headquartered in Ipswich, Suffolk, it was formerly known as Edward Packard and Company Ltd, and Packard and James Fison (Thetford) Limited. It was acquired by Rhône-Poulenc in 1995.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fletcher, Burrows and Company</td>
<td style="text-align: left;">/wiki/Fletcher,_Burrows_and_Company</td>
<td style="text-align: left;">Fletcher, Burrows and Company</td>
<td style="text-align: left;">Fletcher, Burrows and Company</td>
<td style="text-align: left;">Fletcher, Burrows and Company — coal mining, and cotton mills company, 1872–1929. It became part of Manchester Collieries.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Flow Energy</td>
<td style="text-align: left;">/wiki/Flow_Energy</td>
<td style="text-align: left;">Flow Energy</td>
<td style="text-align: left;">Flow Energy</td>
<td style="text-align: left;">Flow Energy — energy company (gas and electricity, boilers). Established in 1998, its headquarters is in Ipswich. It was originally part of Flowgroup plc. In 2018 it was acquired by Co-op Energy.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Focus Films</td>
<td style="text-align: left;">/wiki/Focus_Films</td>
<td style="text-align: left;">Focus Films</td>
<td style="text-align: left;">Focus Films</td>
<td style="text-align: left;">Focus Films — film production company. Established in 1982, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">FoolishPeople</td>
<td style="text-align: left;">/wiki/FoolishPeople</td>
<td style="text-align: left;">FoolishPeople</td>
<td style="text-align: left;">FoolishPeople</td>
<td style="text-align: left;">FoolishPeople — theatre company, film production, and book publishing company, established in 1989.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Modern Life?</td>
<td style="text-align: left;">/wiki/Modern_Life%3F</td>
<td style="text-align: left;">Modern Life?</td>
<td style="text-align: left;">Modern Life?</td>
<td style="text-align: left;">For This Is Film — film production company. See Modern Life?.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Force Protection Europe</td>
<td style="text-align: left;">/wiki/Force_Protection_Europe</td>
<td style="text-align: left;">Force Protection Europe</td>
<td style="text-align: left;">Force Protection Europe</td>
<td style="text-align: left;">Force Protection Europe — military vehicle manufacturing company. Established in 2008, its headquarters is in Leamington Spa, Warwickshire. In 2011 it was purchased by General Dynamic.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Foster Yeoman</td>
<td style="text-align: left;">/wiki/Foster_Yeoman</td>
<td style="text-align: left;">Foster Yeoman</td>
<td style="text-align: left;">Foster Yeoman</td>
<td style="text-align: left;">Foster Yeoman — construction (quarrying and asphalt), and rail haulage company, 1923–2006. Headquartered in Marston Bigot, Somerset, it was merged into Aggregate Industries.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Framestore</td>
<td style="text-align: left;">/wiki/Framestore</td>
<td style="text-align: left;">Framestore</td>
<td style="text-align: left;">Framestore</td>
<td style="text-align: left;">Framestore — film visual effects company. Established in 1986, its headquarters is in London. It was merged with Computer Film Company.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Frank PR</td>
<td style="text-align: left;">/wiki/Frank_PR</td>
<td style="text-align: left;">Frank PR</td>
<td style="text-align: left;">Frank PR</td>
<td style="text-align: left;">Frank PR — public relations company. Established in 2000, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Free Seed Films</td>
<td style="text-align: left;">/wiki/Free_Seed_Films</td>
<td style="text-align: left;">Free Seed Films</td>
<td style="text-align: left;">Free Seed Films</td>
<td style="text-align: left;">Free Seed Films — film production company, established in 2012.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Caparo Vehicle Technologies</td>
<td style="text-align: left;">/wiki/Caparo_Vehicle_Technologies</td>
<td style="text-align: left;">Caparo Vehicle Technologies</td>
<td style="text-align: left;">Caparo Vehicle Technologies</td>
<td style="text-align: left;">Freestream — automotive and aerospace engineering company. See Caparo Vehicle Technologies.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Freud Communications</td>
<td style="text-align: left;">/wiki/Freud_Communications</td>
<td style="text-align: left;">Freud Communications</td>
<td style="text-align: left;">Freud Communications</td>
<td style="text-align: left;">Freud Communications — public relations company. Established in 1985, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fulhold Pharma</td>
<td style="text-align: left;">/wiki/Fulhold_Pharma</td>
<td style="text-align: left;">Fulhold Pharma</td>
<td style="text-align: left;">Fulhold Pharma</td>
<td style="text-align: left;">Fulhold Pharma — pharmaceuticals company. Established in 2014, its headquarters is in Macclesfield, Cheshire. It was formerly known as Fulhold Ltd.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Co-op Funeralcare</td>
<td style="text-align: left;">/wiki/Co-op_Funeralcare</td>
<td style="text-align: left;">Funeral Services Ltd</td>
<td style="text-align: left;">Funeral Services Ltd</td>
<td style="text-align: left;">Funeral Services Ltd (trading as Co-op Funeralcare) — funeral services company (funerals, crematoria and cemeteries, memorial masonry, and coffin production). Headquartered in Manchester, its parent company is The Co-operative Group.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Fuse Universal</td>
<td style="text-align: left;">/wiki/Fuse_Universal</td>
<td style="text-align: left;">Fuse Universal</td>
<td style="text-align: left;">Fuse Universal</td>
<td style="text-align: left;">Fuse Universal — learning solutions company. Established in 2008, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">G.B. Samuelson Productions</td>
<td style="text-align: left;">/wiki/G.B._Samuelson_Productions</td>
<td style="text-align: left;">G.B. Samuelson Productions</td>
<td style="text-align: left;">G.B. Samuelson Productions</td>
<td style="text-align: left;">G.B. Samuelson Productions — film production company, 1914–1933. It was also known as British-Super Films, and Napoleon Films.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Gainsborough Pictures</td>
<td style="text-align: left;">/wiki/Gainsborough_Pictures</td>
<td style="text-align: left;">Gainsborough Pictures</td>
<td style="text-align: left;">Gainsborough Pictures</td>
<td style="text-align: left;">Gainsborough Pictures — film production company, 1924–1951. Established in London, it was also known as Gainsborough Studios.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Gala Bingo</td>
<td style="text-align: left;">/wiki/Gala_Bingo</td>
<td style="text-align: left;">Gala Bingo</td>
<td style="text-align: left;">Gala Bingo</td>
<td style="text-align: left;">Gala Bingo — bingo company, established in 1991.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Galpharm International</td>
<td style="text-align: left;">/wiki/Galpharm_International</td>
<td style="text-align: left;">Galpharm International</td>
<td style="text-align: left;">Galpharm International</td>
<td style="text-align: left;">Galpharm International — pharmaceuticals company (non-prescription medicine). Established in 1982, its headquarters is in Dodworth, Barnsley. In 2008 it was acquired by Perrigo Group.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Galvani Bioelectronics</td>
<td style="text-align: left;">/wiki/Galvani_Bioelectronics</td>
<td style="text-align: left;">Galvani Bioelectronics</td>
<td style="text-align: left;">Galvani Bioelectronics</td>
<td style="text-align: left;">Galvani Bioelectronics — bioelectronics R&amp;D company. Established in 2016 by GlaxoSmithKline and Verily Life Sciences, its headquarters is in Stevenage, Hertfordshire.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Gamesys</td>
<td style="text-align: left;">/wiki/Gamesys</td>
<td style="text-align: left;">Gamesys</td>
<td style="text-align: left;">Gamesys</td>
<td style="text-align: left;">Gamesys — gambling company. Established in 2001, its headquarters is in London. In 2019 its revenue was £415 million, with net income of £8.5 million.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Gas Light and Coke Company</td>
<td style="text-align: left;">/wiki/Gas_Light_and_Coke_Company</td>
<td style="text-align: left;">Gas Light and Coke Company</td>
<td style="text-align: left;">Gas Light and Coke Company</td>
<td style="text-align: left;">Gas Light and Coke Company — energy company (coal gas and coke), 1812–1949. Headquartered in Westminster, London, it was also known as the Westminster Gas Light and Coke Company, and as Chartered Gas Light and Coke Company. In 1949 it was nationalised to become part of the North Thames Gas Board.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Gate Studios</td>
<td style="text-align: left;">/wiki/Gate_Studios</td>
<td style="text-align: left;">Gate Studios</td>
<td style="text-align: left;">Gate Studios</td>
<td style="text-align: left;">Gate Studios — film studios company, 1924—early 1950s. It was situated in Borehamwood.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Gateway Films</td>
<td style="text-align: left;">/wiki/Gateway_Films</td>
<td style="text-align: left;">Gateway Films</td>
<td style="text-align: left;">Gateway Films</td>
<td style="text-align: left;">Gateway Films — film production company. Established in 2009, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Gaumont-British</td>
<td style="text-align: left;">/wiki/Gaumont-British</td>
<td style="text-align: left;">Gaumont British Picture Corporation</td>
<td style="text-align: left;">Gaumont British Picture Corporation</td>
<td style="text-align: left;">Gaumont British Picture Corporation — film company (film production and distribution, cinema chain, film projection equipment manufacturer). Established in 1898, its headquarters was in London. In 1941 it was acquired by The Rank Organisation.</td>
</tr>
<tr class="even">
<td style="text-align: left;">GCM Resources</td>
<td style="text-align: left;">/wiki/GCM_Resources</td>
<td style="text-align: left;">GCM Resources</td>
<td style="text-align: left;">GCM Resources</td>
<td style="text-align: left;">GCM Resources — mining company (open cast coal mining in Bangladesh). Established in 1998, its headquarters is in London. It was formerly known as Asia Energy plc, and as Global Coal Management.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Gemfields</td>
<td style="text-align: left;">/wiki/Gemfields</td>
<td style="text-align: left;">Gemfields</td>
<td style="text-align: left;">Gemfields</td>
<td style="text-align: left;">Gemfields — mining and jewellery company, established in 2007.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Genus plc</td>
<td style="text-align: left;">/wiki/Genus_plc</td>
<td style="text-align: left;">Genus plc</td>
<td style="text-align: left;">Genus plc</td>
<td style="text-align: left;">Genus plc — biotechnology company (producer of biotechnology products for cattle and pigs). Established in 1933, its headquarters is in Basingstoke, Hampshire. It was formerly the Breeding and Production Division of the Milk Marketing Board. In 2019 its revenue was £488 million, with net income of £6.7 million.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lister Motor Company</td>
<td style="text-align: left;">/wiki/Lister_Motor_Company</td>
<td style="text-align: left;">Lister Motor Company</td>
<td style="text-align: left;">Lister Motor Company</td>
<td style="text-align: left;">George Lister Engineering — automobile manufacturing company (sports cars). See Lister Motor Company.</td>
</tr>
<tr class="even">
<td style="text-align: left;">George Wimpey</td>
<td style="text-align: left;">/wiki/George_Wimpey</td>
<td style="text-align: left;">George Wimpey</td>
<td style="text-align: left;">George Wimpey</td>
<td style="text-align: left;">George Wimpey — multinational construction company (housebuilding, civil and commercial construction, formerly road surfacing). Established in 1880, its headquarters is in London. In 2007 it was merged with Taylor Woodrow to form Taylor Wimpey.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Gibbs and Canning Limited</td>
<td style="text-align: left;">/wiki/Gibbs_and_Canning_Limited</td>
<td style="text-align: left;">Gibbs and Canning Limited</td>
<td style="text-align: left;">Gibbs and Canning Limited</td>
<td style="text-align: left;">Gibbs and Canning Limited — terracotta manufacturing company (particularly architectural terracotta), 1847–1950s. Its headquarters was in Glascote, Tamworth, Staffordshire.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Ginetta Cars</td>
<td style="text-align: left;">/wiki/Ginetta_Cars</td>
<td style="text-align: left;">Ginetta Cars</td>
<td style="text-align: left;">Ginetta Cars</td>
<td style="text-align: left;">Ginetta Cars — automobile manufacturing company (racing and sports cars). Established in 1958, its headquarters is in Garforth, Leeds.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">GK Films</td>
<td style="text-align: left;">/wiki/GK_Films</td>
<td style="text-align: left;">GK Films</td>
<td style="text-align: left;">GK Films</td>
<td style="text-align: left;">GK Films — film and TV production company. Established in 1990, it was formerly known as Initial Entertainment Group.</td>
</tr>
<tr class="even">
<td style="text-align: left;">GlaxoSmithKline</td>
<td style="text-align: left;">/wiki/GlaxoSmithKline</td>
<td style="text-align: left;">GlaxoSmithKline</td>
<td style="text-align: left;">GlaxoSmithKline</td>
<td style="text-align: left;">GlaxoSmithKline — British multinational pharmaceutical company (pharmaceuticals, vaccines, oral healthcare, nutritional products, over the counter medicine). It was established in 2000 by a merger of Glaxo Wellcome and SmithKline Beecham. Headquartered in Brentford, London, it has one subsidiary. In 2019 its revenue was £33.7 billion, with net income of £4.6 billion.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Glencore</td>
<td style="text-align: left;">/wiki/Glencore</td>
<td style="text-align: left;">Glencore</td>
<td style="text-align: left;">Glencore</td>
<td style="text-align: left;">Glencore — British / Swiss multinational commodities trading, and mining company. Established in 1974, it was formerly known as Marc Rich + Co AG. Its headquarters is in Baar, Switzerland. In 2019 its revenue was $215 billion, with net income of $1.5 billion.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Glory Film Co.</td>
<td style="text-align: left;">/wiki/Glory_Film_Co.</td>
<td style="text-align: left;">Glory Film Co.</td>
<td style="text-align: left;">Glory Film Co.</td>
<td style="text-align: left;">Glory Film Co. — film and TV production company.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Goldcrest Films</td>
<td style="text-align: left;">/wiki/Goldcrest_Films</td>
<td style="text-align: left;">Goldcrest Films</td>
<td style="text-align: left;">Goldcrest Films</td>
<td style="text-align: left;">Goldcrest Films — film company (film production, distribution, and financing). Established in 1977, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Good Relations</td>
<td style="text-align: left;">/wiki/Good_Relations</td>
<td style="text-align: left;">Good Relations</td>
<td style="text-align: left;">Good Relations</td>
<td style="text-align: left;">Good Relations — public relations company, headquartered in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">GPO Film Unit</td>
<td style="text-align: left;">/wiki/GPO_Film_Unit</td>
<td style="text-align: left;">GPO Film Unit</td>
<td style="text-align: left;">GPO Film Unit</td>
<td style="text-align: left;">GPO Film Unit film production company 1933–1940. It later became Crown Film Unit.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Cartoon Network Studios Europe</td>
<td style="text-align: left;">/wiki/Cartoon_Network_Studios_Europe</td>
<td style="text-align: left;">Cartoon Network Studios Europe</td>
<td style="text-align: left;">Cartoon Network Studios Europe</td>
<td style="text-align: left;">Great Marlborough Productions — animation studio company. See Cartoon Network Studios Europe.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Grain Media</td>
<td style="text-align: left;">/wiki/Grain_Media</td>
<td style="text-align: left;">Grain Media</td>
<td style="text-align: left;">Grain Media</td>
<td style="text-align: left;">Grain Media — film and TV production company. Established in 2006, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Grand Junction Waterworks Company</td>
<td style="text-align: left;">/wiki/Grand_Junction_Waterworks_Company</td>
<td style="text-align: left;">Grand Junction Waterworks Company</td>
<td style="text-align: left;">Grand Junction Waterworks Company</td>
<td style="text-align: left;">Grand Junction Waterworks Company — utility company (water), 1811–1903. Headquartered in London, it became part of the Metropolitan Water Board.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Grand Metropolitan</td>
<td style="text-align: left;">/wiki/Grand_Metropolitan</td>
<td style="text-align: left;">Grand Metropolitan</td>
<td style="text-align: left;">Grand Metropolitan</td>
<td style="text-align: left;">Grand Metropolitan — leisure, manufacturing, and property conglomerate (hotels, holiday centres, catering, restaurants, brewing, dairies, bingo, gambling), 1934–1997. Headquartered in London, it was formerly known as Mount Royal Metropolitan Association (MRMA), and Grand Metropolitan Hotels. In 1997 it was merged with Guinness Brewery to form Diageo plc.</td>
</tr>
<tr class="even">
<td style="text-align: left;">TVR</td>
<td style="text-align: left;">/wiki/TVR</td>
<td style="text-align: left;">TVR</td>
<td style="text-align: left;">TVR</td>
<td style="text-align: left;">Grantura Engineering — see TVR.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">TVR</td>
<td style="text-align: left;">/wiki/TVR</td>
<td style="text-align: left;">TVR</td>
<td style="text-align: left;">TVR</td>
<td style="text-align: left;">Grantura Plastics — see TVR.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Great Productions</td>
<td style="text-align: left;">/wiki/Great_Productions</td>
<td style="text-align: left;">Great Productions</td>
<td style="text-align: left;">Great Productions</td>
<td style="text-align: left;">Great Productions — is a film production company, headquartered at Pinewood Studios.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Essex and Suffolk Water</td>
<td style="text-align: left;">/wiki/Essex_and_Suffolk_Water#Suffolk_Water_plc</td>
<td style="text-align: left;">Great Yarmouth Waterworks Company</td>
<td style="text-align: left;">Great Yarmouth Waterworks Company</td>
<td style="text-align: left;">Great Yarmouth Waterworks Company — was a utility company (water supply) from 1853 to 1962. In 1962 it merged with the Lowestoft Water Company to form the East Anglian Water Company.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Greenpark Productions</td>
<td style="text-align: left;">/wiki/Greenpark_Productions</td>
<td style="text-align: left;">Greenpark Productions</td>
<td style="text-align: left;">Greenpark Productions</td>
<td style="text-align: left;">Greenpark Productions – is a documentary film production company. Established in 1938 in Polperro, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Greybull Capital</td>
<td style="text-align: left;">/wiki/Greybull_Capital</td>
<td style="text-align: left;">Greybull Capital</td>
<td style="text-align: left;">Greybull Capital</td>
<td style="text-align: left;">Greybull Capital — is a private investment company (purchasing and divesting distressed companies). Established in 2010, its headquarters is in Knightsbridge, London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Grinnall Specialist Cars</td>
<td style="text-align: left;">/wiki/Grinnall_Specialist_Cars</td>
<td style="text-align: left;">Grinnall Specialist Cars</td>
<td style="text-align: left;">Grinnall Specialist Cars</td>
<td style="text-align: left;">Grinnall Specialist Cars — is an automobile and motorcycle manufacturing company, established in Bewdley, Worcestershire.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Grosvenor Casinos</td>
<td style="text-align: left;">/wiki/Grosvenor_Casinos</td>
<td style="text-align: left;">Grosvenor Casinos</td>
<td style="text-align: left;">Grosvenor Casinos</td>
<td style="text-align: left;">Grosvenor Casinos — is a gambling company. Established in 1970, its headquarters is in Maidenhead. Its parent company is The Rank Group.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lotus Cars</td>
<td style="text-align: left;">/wiki/Lotus_Cars</td>
<td style="text-align: left;">Lotus Cars</td>
<td style="text-align: left;">Lotus Cars</td>
<td style="text-align: left;">Group Lotus - is a manufacturing company (production of sports and racing cars, and engineering development). See Lotus Cars.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">GTM Cars</td>
<td style="text-align: left;">/wiki/GTM_Cars</td>
<td style="text-align: left;">GTM Cars</td>
<td style="text-align: left;">GTM Cars</td>
<td style="text-align: left;">GTM Cars — is a kit car manufacturing company. Established in 1967, its headquarters is in Kingswinford, Dudley.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Gü</td>
<td style="text-align: left;">/wiki/G%C3%BC</td>
<td style="text-align: left;">Gü</td>
<td style="text-align: left;">Gü</td>
<td style="text-align: left;">Gü – is a dessert manufacturing company that was founded by James Averdieck in 2003 in London. In 2010 Gü was sold to Noble Foods.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">GW Pharmaceuticals</td>
<td style="text-align: left;">/wiki/GW_Pharmaceuticals</td>
<td style="text-align: left;">GW Pharmaceuticals</td>
<td style="text-align: left;">GW Pharmaceuticals</td>
<td style="text-align: left;">GW Pharmaceuticals — is a biopharmaceutical medicines production company. Established in 1998, its headquarters is in Cambridge, Cambridgeshire.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Habitat (retailer)</td>
<td style="text-align: left;">/wiki/Habitat_(retailer)</td>
<td style="text-align: left;">Habitat</td>
<td style="text-align: left;">Habitat</td>
<td style="text-align: left;">Habitat — is a household furnishings retail company. Established in 1964, its headquarters is in Milton Keynes, Buckinghamshire. Its parent company is Sainsbury’s.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Hafren Dyfrdwy</td>
<td style="text-align: left;">/wiki/Hafren_Dyfrdwy</td>
<td style="text-align: left;">Hafren Dyfrdwy</td>
<td style="text-align: left;">Hafren Dyfrdwy</td>
<td style="text-align: left;">Hafren Dyfrdwy — is a utility company (water supply). Established in 1997, its headquarters is in Packsaddle, Rhostyllen, Wrexham, Wales. It was formed from the merger of Wrexham Water plc and Chester Waterworks Company, and was formerly known as Dee Valley Water. Its parent company is Severn Trent.</td>
</tr>
<tr class="even">
<td style="text-align: left;">HAL Films</td>
<td style="text-align: left;">/wiki/HAL_Films</td>
<td style="text-align: left;">HAL Films</td>
<td style="text-align: left;">HAL Films</td>
<td style="text-align: left;">HAL Films — was a film production company from 1997 to 2012. Its headquarters was in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Halifax (bank)</td>
<td style="text-align: left;">/wiki/Halifax_(bank)</td>
<td style="text-align: left;">Halifax</td>
<td style="text-align: left;">Halifax</td>
<td style="text-align: left;">Halifax — is a financial services company (banking and insurance). It was formerly a building society, and estate agents. Established in 1853, its headquarters is in Halifax, West Yorkshire. It was formerly known as the Halifax Permanent Benefit Building and Investment Society, and HBOS. From 2007 it was subsumed by the Bank of Scotland but continued as a brand name.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Halogen Communications</td>
<td style="text-align: left;">/wiki/Halogen_Communications</td>
<td style="text-align: left;">Halogen Communications</td>
<td style="text-align: left;">Halogen Communications</td>
<td style="text-align: left;">Halogen Communications — is a communications company. Established in 2002, its headquarters is in Edinburgh.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Hammer &amp; Tongs</td>
<td style="text-align: left;">/wiki/Hammer_%26_Tongs</td>
<td style="text-align: left;">Hammer &amp; Tongs</td>
<td style="text-align: left;">Hammer &amp; Tongs</td>
<td style="text-align: left;">Hammer &amp; Tongs — is a film and video production company.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Hammer Film Productions</td>
<td style="text-align: left;">/wiki/Hammer_Film_Productions</td>
<td style="text-align: left;">Hammer Film Productions</td>
<td style="text-align: left;">Hammer Film Productions</td>
<td style="text-align: left;">Hammer Film Productions — is a film and television production company. Established in 1934, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HandMade Films</td>
<td style="text-align: left;">/wiki/HandMade_Films</td>
<td style="text-align: left;">HandMade Films</td>
<td style="text-align: left;">HandMade Films</td>
<td style="text-align: left;">HandMade Films — is a film production and distribution company. Established in 1978, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Hanson plc</td>
<td style="text-align: left;">/wiki/Hanson_plc</td>
<td style="text-align: left;">Hanson plc</td>
<td style="text-align: left;">Hanson plc</td>
<td style="text-align: left;">Hanson plc — is a building materials company. It was formerly a conglomerate including Imperial Tobacco, The Energy Group, Millennium Chemicals and others. It was also an asset trader, buying, restructuring and selling companies. Established in 1964, its headquarters is in London. It was formerly known as Hanson Trust. Its parent company is Heidelberg Cement.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Harrison Ainslie</td>
<td style="text-align: left;">/wiki/Harrison_Ainslie</td>
<td style="text-align: left;">Harrison Ainslie</td>
<td style="text-align: left;">Harrison Ainslie</td>
<td style="text-align: left;">Harrison Ainslie — was an iron production, and mining company from 1893 to 1913. It became the Charcoal Iron Company.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Hartlepool Water</td>
<td style="text-align: left;">/wiki/Hartlepool_Water</td>
<td style="text-align: left;">Hartlepool Water</td>
<td style="text-align: left;">Hartlepool Water</td>
<td style="text-align: left;">Hartlepool Water — is a utility company (water supply). Formerly, it was also a gas supplier. Established in 1846, its headquarters is in Huntingdon, Cambridgeshire. It was formerly known as Hartlepool Gas and Water Company. Since 1997 it is owned by Anglian Water.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Hawk Films</td>
<td style="text-align: left;">/wiki/Hawk_Films</td>
<td style="text-align: left;">Hawk Films</td>
<td style="text-align: left;">Hawk Films</td>
<td style="text-align: left;">Hawk Films — is a film production company established in 1964.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Haydock Collieries</td>
<td style="text-align: left;">/wiki/Haydock_Collieries</td>
<td style="text-align: left;">Haydock Collieries</td>
<td style="text-align: left;">Haydock Collieries</td>
<td style="text-align: left;">Haydock Collieries — is a coal mining company, 1899–1947. It became part of the National Coal Board.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Headline Pictures</td>
<td style="text-align: left;">/wiki/Headline_Pictures</td>
<td style="text-align: left;">Headline Pictures</td>
<td style="text-align: left;">Headline Pictures</td>
<td style="text-align: left;">Headline Pictures — is a film and television production company. Established in 2005, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Healthcare at Home</td>
<td style="text-align: left;">/wiki/Healthcare_at_Home</td>
<td style="text-align: left;">Healthcare at Home</td>
<td style="text-align: left;">Healthcare at Home</td>
<td style="text-align: left;">Healthcare at Home — is a pharmaceuticals supply company. Established in 1992, its headquarters is in Burton upon Trent, Staffordshire.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lionsgate UK</td>
<td style="text-align: left;">/wiki/Lionsgate_UK</td>
<td style="text-align: left;">Lionsgate UK</td>
<td style="text-align: left;">Lionsgate UK</td>
<td style="text-align: left;">Helkon SK — film production and distribution company. See Lionsgate UK.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Hemdale Film Corporation</td>
<td style="text-align: left;">/wiki/Hemdale_Film_Corporation</td>
<td style="text-align: left;">Hemdale Film Corporation</td>
<td style="text-align: left;">Hemdale Film Corporation</td>
<td style="text-align: left;">Hemdale Film Corporation — was a film production and distribution company from 1967 to 1995. Headquartered in London, it was later known as Hemdale Communications.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Henleys</td>
<td style="text-align: left;">/wiki/Henleys</td>
<td style="text-align: left;">Henleys Clothing</td>
<td style="text-align: left;">Henleys Clothing</td>
<td style="text-align: left;">Henleys Clothing — was a men and womenswear company (clothes and shoes) from 1996 to 2011. Its headquarters was in Manchester.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Henry’s House (PR firm)</td>
<td style="text-align: left;">/wiki/Henry%27s_House_(PR_firm)</td>
<td style="text-align: left;">Henry’s House</td>
<td style="text-align: left;">Henry’s House</td>
<td style="text-align: left;">Henry’s House — is a public relations company. Established in 1998, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Heyday Films</td>
<td style="text-align: left;">/wiki/Heyday_Films</td>
<td style="text-align: left;">Heyday Films</td>
<td style="text-align: left;">Heyday Films</td>
<td style="text-align: left;">Heyday Films — is a film production company. Established in 1996, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">HICL Infrastructure Company</td>
<td style="text-align: left;">/wiki/HICL_Infrastructure_Company</td>
<td style="text-align: left;">HICL Infrastructure Company</td>
<td style="text-align: left;">HICL Infrastructure Company</td>
<td style="text-align: left;">HICL Infrastructure Company — is an investment trust company (infrastructure investments). It was established in 2006.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Hi-Gen Power</td>
<td style="text-align: left;">/wiki/Hi-Gen_Power</td>
<td style="text-align: left;">Hi-Gen Power</td>
<td style="text-align: left;">Hi-Gen Power</td>
<td style="text-align: left;">Hi-Gen Power — was an energy company (alternative energy). Established in 2009, it is now defunct. Its headquarters was in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Hochschild Mining</td>
<td style="text-align: left;">/wiki/Hochschild_Mining</td>
<td style="text-align: left;">Hochschild Mining</td>
<td style="text-align: left;">Hochschild Mining</td>
<td style="text-align: left;">Hochschild Mining — is a silver and gold mining company. Established in 1911, its headquarters is in London. In 2019 its revenue was $755 million, with total income of $41 million.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Horizon Discovery</td>
<td style="text-align: left;">/wiki/Horizon_Discovery</td>
<td style="text-align: left;">Horizon Discovery</td>
<td style="text-align: left;">Horizon Discovery</td>
<td style="text-align: left;">Horizon Discovery — is a biotechnology company (gene editing, producing genetically modified cells and organisms). Established in 2005, its headquarters is in Cambridge.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Hovis</td>
<td style="text-align: left;">/wiki/Hovis</td>
<td style="text-align: left;">Hovis</td>
<td style="text-align: left;">Hovis</td>
<td style="text-align: left;">Hovis – is a limited company that produces flour and bread and licenses the production of Hovis Biscuits. It was founded in Stoke-on-Trent before mass production began in Macclesfield, Cheshire in 1886. It became part of Rank Hovis McDougall in 1962, was purchased by Premier Foods in 2007 and is now owned by Endless LLP. It is now headquartered in High Wycombe, Buckinghamshire.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Hulton Colliery Company</td>
<td style="text-align: left;">/wiki/Hulton_Colliery_Company</td>
<td style="text-align: left;">Hulton Colliery Company</td>
<td style="text-align: left;">Hulton Colliery Company</td>
<td style="text-align: left;">Hulton Colliery Company — was a coal mining company. Established in 1858, it is now defunct.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Huntsworth</td>
<td style="text-align: left;">/wiki/Huntsworth</td>
<td style="text-align: left;">Huntsworth</td>
<td style="text-align: left;">Huntsworth</td>
<td style="text-align: left;">Huntsworth — is a public relations company. Established in 1974, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Hurricane Films</td>
<td style="text-align: left;">/wiki/Hurricane_Films</td>
<td style="text-align: left;">Hurricane Films</td>
<td style="text-align: left;">Hurricane Films</td>
<td style="text-align: left;">Hurricane Films — is a film production company. Established in 2000, its headquarters is in Liverpool.</td>
</tr>
<tr class="even">
<td style="text-align: left;">IAG Cargo</td>
<td style="text-align: left;">/wiki/IAG_Cargo</td>
<td style="text-align: left;">IAG Cargo</td>
<td style="text-align: left;">IAG Cargo</td>
<td style="text-align: left;">IAG Cargo — is a cargo airline company. Established in 2011, it was formed from the merger of British Airways World Cargo and Iberia Cargo. Its parent company is International Airlines Group.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Ideal Film Company</td>
<td style="text-align: left;">/wiki/Ideal_Film_Company</td>
<td style="text-align: left;">Ideal Film Company</td>
<td style="text-align: left;">Ideal Film Company</td>
<td style="text-align: left;">Ideal Film Company (aka Ideal Films) — was a film production and distribution company from 1911 to 1934. Its headquarters was in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">IG Group</td>
<td style="text-align: left;">/wiki/IG_Group</td>
<td style="text-align: left;">IG Group</td>
<td style="text-align: left;">IG Group</td>
<td style="text-align: left;">IG Group — is a financial services company. Established in 1974, its headquarters is in London. In 2019 its revenue was £488 million, with net income of £158 million.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">The Imaginarium</td>
<td style="text-align: left;">/wiki/The_Imaginarium</td>
<td style="text-align: left;">The Imaginarium</td>
<td style="text-align: left;">The Imaginarium</td>
<td style="text-align: left;">The Imaginarium (aka Imaginarium Productions) — is a film production and performance capture company. Established in 2011, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Immunocore</td>
<td style="text-align: left;">/wiki/Immunocore</td>
<td style="text-align: left;">Immunocore</td>
<td style="text-align: left;">Immunocore</td>
<td style="text-align: left;">Immunocore — is a biotechnology company (biological drugs). Established in 2008, its headquarters is in Oxford.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Imperial Brands</td>
<td style="text-align: left;">/wiki/Imperial_Brands</td>
<td style="text-align: left;">Imperial Brands</td>
<td style="text-align: left;">Imperial Brands</td>
<td style="text-align: left;">Imperial Brands - is a multinational tobacco company also involved in logistics through one of its 5 subsidiaries Logista. It was established in 1901 through the amalgamation of 13 separate tobacco companies to form Imperial Tobacco Group. Headquartered in Bristol, its 2020 revenue was £32.5 billion, with a net income of £1.5 billion.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Imperial Chemical Industries</td>
<td style="text-align: left;">/wiki/Imperial_Chemical_Industries</td>
<td style="text-align: left;">Imperial Chemical Industries</td>
<td style="text-align: left;">Imperial Chemical Industries</td>
<td style="text-align: left;">Imperial Chemical Industries (ICI) — is a chemicals manufacturing company (paints, pharmaceuticals, polymers, food ingredients, electronic materials, agrochemicals, fabrics, motorcycles), 1926–2008. Headquartered in London, in 2008 it was acquired by Akzo Nobel.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">John and James Woolf</td>
<td style="text-align: left;">/wiki/John_and_James_Woolf</td>
<td style="text-align: left;">Independent Film Distribution</td>
<td style="text-align: left;">Independent Film Distribution</td>
<td style="text-align: left;">Independent Film Distribution — was a film distribution company from 1950 to 1959.</td>
</tr>
<tr class="even">
<td style="text-align: left;">GK Films</td>
<td style="text-align: left;">/wiki/GK_Films</td>
<td style="text-align: left;">GK Films</td>
<td style="text-align: left;">GK Films</td>
<td style="text-align: left;">Initial Entertainment Group - was a film and television production company. See GK Films.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Intermediate Capital Group</td>
<td style="text-align: left;">/wiki/Intermediate_Capital_Group</td>
<td style="text-align: left;">Intermediate Capital Group</td>
<td style="text-align: left;">Intermediate Capital Group</td>
<td style="text-align: left;">Intermediate Capital Group (iCG) - is a private equity investment firm whose activities include financial services and asset management. Established in 1989, its headquarters is in London. As of 2020 it has €45 billion of assets under management. Its 2020 revenue was £413 million, with a net income of £110.6 million.</td>
</tr>
<tr class="even">
<td style="text-align: left;">International Airlines Group</td>
<td style="text-align: left;">/wiki/International_Airlines_Group</td>
<td style="text-align: left;">International Airlines Group</td>
<td style="text-align: left;">International Airlines Group</td>
<td style="text-align: left;">International Airlines Group (AIG; its full name is International Consolidated Airlines Group) — is an Anglo-Spanish multinational airlines holding company. Established in 2011, its headquarters are in London and Madrid, Spain. It was formed from the merger of British Airways and Iberia. In 2019 its revenue was £25.5 billion, with a net income of £1.7 billion.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">International Game Technology</td>
<td style="text-align: left;">/wiki/International_Game_Technology</td>
<td style="text-align: left;">International Game Technology</td>
<td style="text-align: left;">International Game Technology</td>
<td style="text-align: left;">International Game Technology — is a gaming company. Established in 1990, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">Isle of Man Film</td>
<td style="text-align: left;">/wiki/Isle_of_Man_Film</td>
<td style="text-align: left;">Isle of Man Film</td>
<td style="text-align: left;">Isle of Man Film</td>
<td style="text-align: left;">Isle of Man Film — is a film production and finance company. Established in 1995, its headquarters is in the Isle of Man.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">ITC Entertainment</td>
<td style="text-align: left;">/wiki/ITC_Entertainment</td>
<td style="text-align: left;">ITC Entertainment</td>
<td style="text-align: left;">ITC Entertainment</td>
<td style="text-align: left;">ITC Entertainment (aka Incorporated Television Company (ITC)) - was a television and film production and distribution company from 1954 to 1998. Its headquarters was in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">ITH Pharma</td>
<td style="text-align: left;">/wiki/ITH_Pharma</td>
<td style="text-align: left;">ITH Pharma</td>
<td style="text-align: left;">ITH Pharma</td>
<td style="text-align: left;">ITH Pharma — is a pharmaceuticals company (intravenous medication). Established in 2008, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">IXICO</td>
<td style="text-align: left;">/wiki/IXICO</td>
<td style="text-align: left;">IXICO</td>
<td style="text-align: left;">IXICO</td>
<td style="text-align: left;">IXICO — is a biotechnology (data analytics for clinical research). Established in 2004, its headquarters is in London.</td>
</tr>
<tr class="even">
<td style="text-align: left;">JAG Communications</td>
<td style="text-align: left;">/wiki/JAG_Communications</td>
<td style="text-align: left;">JAG Communications</td>
<td style="text-align: left;">JAG Communications</td>
<td style="text-align: left;">JAG Communications — was a mobile phones retail company from 1989 to 2010. It was headquartered at Perranporth, Cornwall.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">James Hay Partnership</td>
<td style="text-align: left;">/wiki/James_Hay_Partnership</td>
<td style="text-align: left;">James Hay Partnership</td>
<td style="text-align: left;">James Hay Partnership</td>
<td style="text-align: left;">James Hay Partnership — is a financial services company (pension products, investment). Established in 1979, its headquarters is in Salisbury, Wiltshire. In 1990 it became part of Abbey National and then Santander UK before being sold to the IFG Group plc in 2010.</td>
</tr>
<tr class="even">
<td style="text-align: left;">James Woolley, Sons and Co.</td>
<td style="text-align: left;">/wiki/James_Woolley,_Sons_and_Co.</td>
<td style="text-align: left;">James Woolley, Sons and Co.</td>
<td style="text-align: left;">James Woolley, Sons and Co.</td>
<td style="text-align: left;">James Woolley, Sons and Co. — was a manufacturing company (pharmaceuticals, surgical equipment, trusses, talcum powder, cordials, photographic equipment), from 1833 to 1962. Headquartered in Manchester, in 1962 it was acquired by British Drug Houses.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">JBA Motors</td>
<td style="text-align: left;">/wiki/JBA_Motors</td>
<td style="text-align: left;">JBA Motors</td>
<td style="text-align: left;">JBA Motors</td>
<td style="text-align: left;">JBA Motors — was a manufacturing company (automobile production) from 1982 to 2007. Established in Norwich, Norfolk, it was later headquartered in Standish, Greater Manchester. It was formerly known as JBA Engineering.</td>
</tr>
<tr class="even">
<td style="text-align: left;">JC Vickery</td>
<td style="text-align: left;">/wiki/JC_Vickery</td>
<td style="text-align: left;">JC Vickery</td>
<td style="text-align: left;">JC Vickery</td>
<td style="text-align: left;">JC Vickery — is a consumer goods company. Established in 1890, its headquarters is in London.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">JD Sports</td>
<td style="text-align: left;">/wiki/JD_Sports</td>
<td style="text-align: left;">JD Sports Fashion</td>
<td style="text-align: left;">JD Sports Fashion</td>
<td style="text-align: left;">JD Sports Fashion - is a sports fashion retail company. Established in 1981, its headquarters is in Burnley, Greater Manchester. It has 23 subsidiaries and is majority owned by Pentland Group. In 2020 its revenue was £6.1 billion, with a net income of £250.7 million.</td>
</tr>
<tr class="even">
<td style="text-align: left;">John Bradley &amp; Co</td>
<td style="text-align: left;">/wiki/John_Bradley_%26_Co</td>
<td style="text-align: left;">John Bradley &amp; Co</td>
<td style="text-align: left;">John Bradley &amp; Co</td>
<td style="text-align: left;">John Bradley &amp; Co — was an ironworks, mining, and freight railway company from 1800 to 1966. Its headquarters was in Stourbridge.</td>
</tr>
<tr class="odd">
<td style="text-align: left;">John Brogden and Sons</td>
<td style="text-align: left;">/wiki/John_Brogden_and_Sons</td>
<td style="text-align: left;">John Brogden and Sons</td>
<td style="text-align: left;">John Brogden and Sons</td>
<td style="text-align: left;">John Brogden and Sons — was a railway contractors, mining, and iron smelting company from 1828 to 1880. Its headquarters was in London.</td>
</tr>
</tbody>
</table>
