because of need to get data as fast as possible we must speedup getiing data
using concurrent processes axios.all will help
Because all servers has specifig limits so sentinelhub has too for 

https://docs.sentinel-hub.com/api/latest/api/overview/rate-limiting/

there ways to update and get the imnage related data
update when navigatinf specifig geometry area first check from sentinel (mitkä ehdot jos tämä päivä on  uudempi kuin 
mikä on viimeisin dates-taulussa/kollectionissa) ja muita kascukaudella!!!
Jos in uusi AOI niin silloin ei tsekata ekana kascukautta ja hylätä "talvella" vaan jos dates-data löytyy niin on kyse pävityksestä ja sillon vain kasvukaudella.
TESTI
Siis geometria on avain ja haetaan dates-päivät sentineliltä jos ei ole kannassa 
jos on kannassa niin haetaan viimeinen päiväys ja verrataan nykypäivään jos ei ole smaat 
niin käydään hakemassa sentinelltä viimeisen dates päiväyksen ja tämän jetken välisesltä ajakta dataa.
testaa kaukanko kestää esim. muutama päivä verratuna koko kasvukauteen hakea!!! 