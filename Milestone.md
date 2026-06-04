Milestone
   
Seznam přečtených článků s uvedením zdrojů:

filtrování a předzpracování gravitačních vln:

https://iopscience.iop.org/article/10.1088/1361-6382/ab685e
    
dokumentace a tutoriál pro práci s gravitačními vlnami:

https://gwpy.github.io/docs/3.0.12/

různé zprávy/články ze soutěže (hlavně pro porovnání):

https://www.kaggle.com/competitions/g2net-gravitational-wave-detection

Stručné shrnutí zadání

Zadáním práce je vytvořit model pro detekti gravitačních vln, na kterým se následně spustí symbolická regrese založená na funkci sin(A_i; \omega_i; t), jejím úkolem bude určení parametrů A a \omega. Přesnější informace v README.

Popis aktuálního postupu práce

Součástí milestonu je zatím pouze pár modelů, které se učily na předzpracovaných datech i na datech syrových neupravených. 2 modely jsou kombinované, jako vstup jsou předzpracovaná data i data neupravená, 1 model poté je naučen pouze na datech neupravených, důvod použití neupravených dat je snaha v datech ponechat vlnu. Předzpracováním, nebo filtrováním se tato vlna odstraňuje, což by poté nemuselo být vhodné pro symbolickou regresi založenou právě na funkci sin.	

Po zpracování gravitační vlny vznikne jakýsi bílý šum, kde pokud senzory vlnu zachytily dobře, tak dochází heteroskedasticitě zpracované časové řady, na jejím krátkém úseku je na první pohled bílý šum s větší variancí oproti zbytku řady. Tento poznatek by podle mého šel použít na vytvoření umělých dat pro jiné modely zaměřené na detekci gravitačních vln.
Dosavadní výsledky

Hlavní dosavadní výsledky jsou 2 modely, residuální 1D CNN. První model má 3 vstupy na nepředzpracovaný data, druhý model má 6 vstupů na předzpracovaná i zpracovaná data, to je jejich jediný rozdíl.

Model, který pracoval pouze na nezpracovaných datech měl znatelně horší výsledky:

Validation Accuracy: 0.5
F1: 0.6682
ROC-AUC: 0.5017

Model, který pracoval nad zpracovanými i nezpracovanými daty poté dosahoval lepších výsledků:

Validation Accuracy: 0.6138
F1: 0.6645
ROC-AUC: 0.7169

Tyto výsledky říkají, že z pohledu modelu je předzpracování důležité, ale předzpracování odstraňuje vlnu samotnou - ponechává pouze časovou řadu připomínající bílý šum. Otázkou tedy zůstává, zda samotná funkce sin dokáže dostatečně vypadat jako signál ze senzorů na gravitační vlny. Další část práce se chci tedy zaměřit na symbolickou regresi pomocí funkce sin, jako ze zadání a případně se pokusím najít funkci lepší, která by gravitační vlny vysvětlovala lépe.

Odkaz na repozitář

https://gitlab.fit.cvut.cz/pokorlu8/mvi-sp
