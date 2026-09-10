# TD-TP : Processus stationnaires (Chapitre 1)

## Partie 1 : Stationnarité

> [!question] Exercice 1 : Stationnarité stricte et faible
> Soit le processus défini par $X_{t} = A \cos(\omega t) + B \sin(\omega t)$, où $A$ et $B$ sont des variables aléatoires indépendantes de moyenne nulle et de variance $\sigma^{2}$, et $\omega$ est une constante.
> 
> 1. Ce processus est-il stationnaire au sens faible ? Justifier.
> 2. Ce processus est-il [[60.1.9. Stationnarité stricte|strictement stationnaire]] ? Justifier (on supposera que $A$ et $B$ suivent une loi normale).
> 
> *Indication : Calculer $\mathbb{E}(X_{t})$, $\operatorname{Var}(X_{t})$ et $\operatorname{Cov}(X_{t}, X_{t+h})$.*

> [!success] Correction détaillée : Exercice 1
> 
> **1. Stationnarité au sens faible (au second ordre) :**
> - **Espérance mathématique :** Par linéarité, comme $\mathbb{E}[A] = \mathbb{E}[B] = 0$ :
>   $$\mathbb{E}[X_t] = \cos(\omega t)\mathbb{E}[A] + \sin(\omega t)\mathbb{E}[B] = 0$$
>   L'espérance est constante et indépendante du temps $t$.
> 
> - **Variance :** Comme $A$ et $B$ sont indépendantes et de variance $\sigma^2$ :
>   $$\operatorname{Var}(X_t) = \cos^2(\omega t)\operatorname{Var}(A) + \sin^2(\omega t)\operatorname{Var}(B) = \sigma^2(\cos^2(\omega t) + \sin^2(\omega t)) = \sigma^2 < \infty$$
>   La variance est finie et constante pour tout $t$.
> 
> - **Autocovariance $\gamma(t, t+h) = \operatorname{Cov}(X_t, X_{t+h})$ :**
>   Comme $\mathbb{E}[X_t] = 0$, $\operatorname{Cov}(X_t, X_{t+h}) = \mathbb{E}[X_t X_{t+h}]$. En développant :
>   $$X_t X_{t+h} = [A \cos(\omega t) + B \sin(\omega t)] [A \cos(\omega(t+h)) + B \sin(\omega(t+h))]$$
>   Comme $\mathbb{E}[A^2] = \mathbb{E}[B^2] = \sigma^2$ et $\mathbb{E}[AB] = \mathbb{E}[A]\mathbb{E}[B] = 0$, l'espérance des termes croisés s'annule :
>   $$\operatorname{Cov}(X_t, X_{t+h}) = \sigma^2 [\cos(\omega t)\cos(\omega(t+h)) + \sin(\omega t)\sin(\omega(t+h))]$$
>   D'après l'identité trigonométrique $\cos(a)\cos(b) + \sin(a)\sin(b) = \cos(a-b)$ :
>   $$\operatorname{Cov}(X_t, X_{t+h}) = \sigma^2 \cos(\omega(t+h) - \omega t) = \sigma^2 \cos(\omega h)$$
>   La covariance ne dépend que du décalage temporel $h$.
> 
> **Conclusion :** Les trois conditions sont vérifiées, le processus $(X_t)$ est **[[60.1.10. Stationnarité faible|faiblement stationnaire]]**.
> 
> ---
> 
> **2. Stationnarité stricte (avec $A, B \sim \mathcal{N}(0, \sigma^2)$ indépendantes) :**
> - Pour tout $k \ge 1$ et toutes dates $(t_1, \dots, t_k)$, le vecteur $(X_{t_1}, \dots, X_{t_k})$ est une combinaison linéaire du vecteur gaussien $(A, B)^T$.
> - C'est donc un **[[60.1.11. Processus Gaussien|processus gaussien]]**.
> - Pour un [[60.1.11. Processus Gaussien|processus gaussien]], la loi conjointe de tout sous-vecteur est entièrement déterminée par son espérance et sa fonction d'autocovariance. Comme ces moments sont invariants par translation temporelle, la loi conjointe de $(X_{t_1+h}, \dots, X_{t_k+h})$ est identique à celle de $(X_{t_1}, \dots, X_{t_k})$.
> 
> **Conclusion :** Sous l'hypothèse de gaussianité de $A$ et $B$, le processus est **[[60.1.9. Stationnarité stricte|strictement stationnaire]]**.

---

> [!question] Exercice 2 : Contre-exemple faible $\not\Rightarrow$ stricte
> Soit $\{A_{t}\}$ une suite i.i.d. $\sim \mathcal{N}(0,1)$ et $\{B_{t}\}$ une suite i.i.d. de loi de Laplace $(0,1)$, indépendantes entre elles. Définissons :
> $$X_{t} = \begin{cases} A_{t}, \quad \text{si } t \text{ pair} \\ B_{t}, \quad \text{si } t \text{ impair} \end{cases}$$
> 
> 1. Montrer que $X_{t}$ est [[60.1.10. Stationnarité faible|faiblement stationnaire]].
> 2. Montrer que $X_{t}$ n'est pas [[60.1.9. Stationnarité stricte|strictement stationnaire]].

> [!success] Correction détaillée : Exercice 2
> 
> **1. Montrons que $X_t$ est [[60.1.10. Stationnarité faible|faiblement stationnaire]] :**
> - **Espérance :**
>   - Si $t$ est pair : $\mathbb{E}[X_t] = \mathbb{E}[A_t] = 0$.
>   - Si $t$ est impair : $\mathbb{E}[X_t] = \mathbb{E}[B_t] = 0$.
>   Donc $\mathbb{E}[X_t] = 0$ pour tout $t \in \mathbb{Z}$.
> 
> - **Variance :**
>   - Si $t$ est pair : $\operatorname{Var}(X_t) = \operatorname{Var}(A_t) = 1$.
>   - Si $t$ est impair : $\operatorname{Var}(X_t) = \operatorname{Var}(B_t) = 1$ (variance unitaire de la loi de Laplace standard).
>   Donc $\operatorname{Var}(X_t) = 1 < \infty$ pour tout $t \in \mathbb{Z}$.
> 
> - **Autocovariance $\gamma(t, t+h)$ pour $h \ne 0$ :**
>   Pour $h \ne 0$, les dates $t$ et $t+h$ sont distinctes. Dès lors, $X_t$ et $X_{t+h}$ proviennent de deux tirages indépendants :
>   - soit deux variables gaussiennes distinctes $A_t$ et $A_{t+h}$ (i.i.d.),
>   - soit deux variables de Laplace distinctes $B_t$ et $B_{t+h}$ (i.i.d.),
>   - soit une gaussienne et une Laplace, indépendantes par hypothèse.
>   Par conséquent, $X_t$ et $X_{t+h}$ sont mutuellement indépendantes :
>   $$\operatorname{Cov}(X_t, X_{t+h}) = 0 \quad \forall h \ne 0$$
>   Ainsi, $\gamma(h) = 1$ si $h = 0$, et $\gamma(h) = 0$ si $h \ne 0$. La fonction d'autocovariance ne dépend que de $h$.
> 
> **Conclusion :** $X_t$ est **[[60.1.10. Stationnarité faible|faiblement stationnaire]]** (c'est un [[60.1.12. Bruit blanc faible|bruit blanc faible]] $BB(0, 1)$).
> 
> ---
> 
> **2. Montrons que $X_t$ n'est pas [[60.1.9. Stationnarité stricte|strictement stationnaire]] :**
> - Pour être [[60.1.9. Stationnarité stricte|strictement stationnaire]], les lois marginales unidimensionnelles de $X_t$ doivent être identiques pour toute date $t$.
> - Or :
>   - Pour $t$ pair : $X_t \sim \mathcal{N}(0, 1)$. Son moment d'ordre 4 vaut $\mathbb{E}[X_t^4] = 3$.
>   - Pour $t$ impair : $X_t$ suit une loi de Laplace centrée de variance 1. Son kurtosis vaut $\mathbb{E}[X_t^4] = 6$.
> - Comme $\mathbb{E}[X_0^4] = 3 \ne 6 = \mathbb{E}[X_1^4]$, la loi de probabilité dépend de la parité de la date $t$.
> 
> **Conclusion :** $X_t$ n'est **pas [[60.1.9. Stationnarité stricte|strictement stationnaire]]**. C'est un contre-exemple canonique montrant que la stationnarité faible n'implique pas la stationnarité stricte.

---

## Partie 2 : ACF et PACF

> [!question] Exercice 3 : Calcul de l'ACF
> Soit le processus $X_{t} = \epsilon_{t} - \epsilon_{t-4}$, où $\epsilon_{t} \sim BB(0, \sigma^{2})$.
> 
> 1. Calculer $\gamma(0)$, $\gamma(4)$, et $\gamma(h)$ pour $h \neq 0, 4$.
> 2. En déduire l'ACF $\rho(h)$.
> 3. Que constatez-vous pour $h = 4$ ?
> 4. Pour des données trimestrielles, que représente ce processus ?
> 
> *Indication : $\gamma(h) = \operatorname{Cov}(X_{t}, X_{t-h})$.*

> [!success] Correction détaillée : Exercice 3
> 
> **1. Calcul des autocovariances $\gamma(h) = \mathbb{E}[X_t X_{t-h}]$ :**
> - **Pour $h = 0$ :**
>   $$\gamma(0) = \operatorname{Var}(\epsilon_t - \epsilon_{t-4}) = \operatorname{Var}(\epsilon_t) + \operatorname{Var}(\epsilon_{t-4}) = \sigma^2 + \sigma^2 = 2\sigma^2$$
> 
> - **Pour $h = 4$ :**
>   $$\gamma(4) = \mathbb{E}[(\epsilon_t - \epsilon_{t-4})(\epsilon_{t-4} - \epsilon_{t-8})]$$
>   $$= \mathbb{E}[\epsilon_t \epsilon_{t-4}] - \mathbb{E}[\epsilon_t \epsilon_{t-8}] - \mathbb{E}[\epsilon_{t-4}^2] + \mathbb{E}[\epsilon_{t-4}\epsilon_{t-8}]$$
>   Comme les bruits à dates différentes sont non corrélés :
>   $$\gamma(4) = 0 - 0 - \sigma^2 + 0 = -\sigma^2$$
>   Par parité de la fonction d'autocovariance, $\gamma(-4) = \gamma(4) = -\sigma^2$.
> 
> - **Pour $|h| \notin \{0, 4\}$ :**
>   Les variables aléatoires impliquées dans $X_t = \epsilon_t - \epsilon_{t-4}$ et $X_{t-h} = \epsilon_{t-h} - \epsilon_{t-h-4}$ portent sur des indices disjoints. Donc :
>   $$\gamma(h) = 0 \quad \forall |h| \notin \{0, 4\}$$
> 
> ---
> 
> **2. Déduction de la fonction d'autocorrélation $\rho(h) = \frac{\gamma(h)}{\gamma(0)}$ :**
> - $\rho(0) = 1$
> - $\rho(4) = \rho(-4) = \frac{-\sigma^2}{2\sigma^2} = -0.5$
> - $\rho(h) = 0$ pour tout $|h| \notin \{0, 4\}$
> 
> ---
> 
> **3. Constat pour $h = 4$ :**
> - On observe une autocorrélation négative marquée $\rho(4) = -0.5$.
> - Cela signifie qu'un choc positif à la période $t-4$ induit mécaniquement une valeur attendue négative 4 périodes plus tard à la période $t$ (effet balancier).
> 
> ---
> 
> **4. Interprétation pour des données trimestrielles :**
> - Avec 4 trimestres par an, $X_t = X_t^{brut} - X_{t-4}^{brut}$ représente la **différenciation saisonnière annuelle** d'ordre 4 :
>   $$X_t = (1 - B^4) Y_t = \nabla_4 Y_t$$
> - Si la série originale $Y_t$ contient une forte composante saisonnière annuelle (par exemple le chiffre d'affaires du trimestre $T$ comparé au même trimestre de l'année précédente), cette différenciation permet d'éliminer la saisonnalité déterministe ou stochastique.

---

> [!question] Exercice 4 : Identification à partir du corrélogramme
> On vous donne les corrélogrammes suivants (ACF et PACF) pour quatre séries différentes. Pour chacune, indiquez le type de processus le plus probable :
> 
> 1. ACF décroît lentement, PACF nulle après $h=1$.
> 2. ACF nulle après $h=2$, PACF décroît lentement.
> 3. ACF décroît lentement, PACF décroît lentement.
> 4. ACF nulle pour tout $h \neq 0$, PACF nulle pour tout $h \neq 0$.

> [!success] Correction détaillée : Exercice 4
> 
> En appliquant la méthodologie d'identification de **Box-Jenkins** basée sur la signature théorique de l'ACF et de la PACF :
> 
> 1. **ACF décroît exponentiellement, PACF coupée après $h=1$ :**
>    - Modèle : **Processus $\text{AR}(1)$**.
>    - *Règle :* La PACF d'un $\text{AR}(p)$ se coupe nettement au retard $p$ (ici $p=1$), tandis que son ACF s'amortit progressivement.
> 
> 2. **ACF coupée après $h=2$, PACF décroît lentement :**
>    - Modèle : **Processus $\text{MA}(2)$**.
>    - *Règle :* L'ACF d'un $\text{MA}(q)$ est strictement nulle pour tout retard $h > q$ (ici $q=2$), tandis que sa PACF s'amortit progressivement.
> 
> 3. **ACF décroît lentement, PACF décroît lentement :**
>    - Modèle : **Processus $\text{ARMA}(p, q)$ mixte** avec $p \ge 1$ et $q \ge 1$.
>    - *Règle :* Ni l'ACF ni la PACF ne présentent de coupure franche ; les deux fonctions s'amortissent sous forme exponentielle ou sinusoïdale amortie.
> 
> 4. **ACF nulle pour tout $h \ne 0$, PACF nulle pour tout $h \ne 0$ :**
>    - Modèle : **Bruit Blanc $\text{BB}(0, \sigma^2)$**.
>    - *Règle :* Absence totale de mémoire sérielle passée ou présente.

---

## Partie 3 : Estimation empirique

> [!question] Exercice 5 : Intervalles de confiance
> Pour une série de $n = 100$ observations, on calcule l'ACF empirique.
> 
> 1. Quelle est la formule de l'intervalle de confiance à 95% pour $\hat{\rho}(h)$ sous l'hypothèse de bruit blanc ?
> 2. Application numérique : $\hat{\rho}(1) = 0.25$, $\hat{\rho}(2) = 0.15$, $\hat{\rho}(3) = 0.30$.
> 3. Quel(s) retard(s) sont significativement différents de 0 ?
> 
> *Indication : Intervalle de confiance : $\pm 1.96 / \sqrt{n}$.*

> [!success] Correction détaillée : Exercice 5
> 
> **1. Formule de l'intervalle de confiance à 95% :**
> - D'après le [[60.1.23. Intervalle de confiance de Bartlett|théorème de Bartlett]], sous l'hypothèse nulle $H_0$ où la série est un bruit blanc, pour tout $h \ge 1$ :
>   $$\sqrt{n} \hat{\rho}(h) \xrightarrow{\mathcal{L}} \mathcal{N}(0, 1)$$
> - L'intervalle de confiance bilatéral au niveau $\alpha = 5\%$ s'écrit :
>   $$IC_{0.95}(\hat{\rho}(h)) = \left[ -\frac{z_{1-\alpha/2}}{\sqrt{n}}, +\frac{z_{1-\alpha/2}}{\sqrt{n}} \right] = \left[ -\frac{1.96}{\sqrt{n}}, +\frac{1.96}{\sqrt{n}} \right]$$
> 
> ---
> 
> **2. Application numérique ($n = 100$) :**
> - Calcul du seuil critique :
>   $$\frac{1.96}{\sqrt{100}} = \frac{1.96}{10} = 0.196$$
> - L'intervalle d'acceptation de $H_0$ est donc :
>   $$[-0.196 \; ; \; +0.196]$$
> 
> ---
> 
> **3. Retards significativement différents de 0 :**
> - Pour $h = 1$ : $\hat{\rho}(1) = 0.25 > 0.196 \implies$ **Significatif** (rejet de $H_0$).
> - Pour $h = 2$ : $\hat{\rho}(2) = 0.15 \in [-0.196, 0.196] \implies$ **Non significatif** (on ne rejette pas $H_0$).
> - Pour $h = 3$ : $\hat{\rho}(3) = 0.30 > 0.196 \implies$ **Significatif** (rejet de $H_0$).
> 
> **Conclusion :** Les autocorrélations aux retards $h = 1$ et $h = 3$ sont statistiquement significatives au seuil de $5\%$.

---

## Partie 4 : Tests de bruit blanc

> [!question] Exercice 6 : Test de Ljung-Box
> On effectue le [[60.1.25. Test de Ljung - Box|test de Ljung-Box]] sur une série de $n = 200$ observations, avec $h = 10$ retards. On obtient une statistique $Q = 18.5$.
> 
> 1. Quelle est la distribution asymptotique de $Q$ sous $H_{0}$ (bruit blanc) ?
> 2. Calculer le seuil critique à 5% (valeur approchée).
> 3. La série est-elle un bruit blanc ?
> 
> *Indication : $\chi_{10, 0.95}^{2} \approx 18.31$.*

> [!success] Correction détaillée : Exercice 6
> 
> **1. Distribution asymptotique de la statistique $Q$ de Ljung-Box :**
> - La statistique $Q$ est définie par :
>   $$Q_{LB} = n(n+2) \sum_{k=1}^h \frac{\hat{\rho}^2(k)}{n-k}$$
> - Sous l'hypothèse nulle $H_0$ (absence d'autocorrélation jusqu'au retard $h$) :
>   $$Q_{LB} \xrightarrow{\mathcal{L}} \chi^2(h)$$
>   Ici, elle suit asymptotiquement une loi du Chi-deux à $h = 10$ degrés de liberté : $\chi^2(10)$.
> 
> ---
> 
> **2. Seuil critique à 5% :**
> - Le quantile d'ordre $1 - \alpha = 0.95$ pour une loi $\chi^2(10)$ est :
>   $$c_{0.05} = \chi_{10, 0.95}^2 \approx 18.31$$
> 
> ---
> 
> **3. Décision du test :**
> - On compare la statistique observée $Q_{obs} = 18.5$ au seuil critique :
>   $$Q_{obs} = 18.5 > 18.31$$
> - La statistique tombe dans la région de rejet $[18.31, +\infty[$.
> 
> **Conclusion :** On **rejette l'hypothèse nulle $H_0$** au niveau de risque $\alpha = 5\%$. La série n'est **pas un bruit blanc** ; il existe une dépendance linéaire globale significative sur les 10 premiers retards.

---

> [!question] Exercice 7 : [[60.1.24. Test de Box - Pierce|Box-Pierce]] vs Ljung-Box
> Pour une série de $n = 50$ observations, on calcule les statistiques de [[60.1.24. Test de Box - Pierce|Box-Pierce]] et de Ljung-Box.
> 
> 4. Quelle est la différence entre les deux tests ?
> 5. Lequel est préférable pour $n$ petit et pourquoi ?

> [!success] Correction détaillée : Exercice 7
> 
> **4. Différence mathématique entre les deux statistiques :**
> - **Statistique de [[60.1.24. Test de Box - Pierce|Box-Pierce]] :**
>   $$Q_{BP} = n \sum_{k=1}^h \hat{\rho}^2(k)$$
>   Elle pondère chaque coefficient empirique au carré de manière uniforme par la taille d'échantillon $n$.
> 
> - **Statistique de Ljung-Box :**
>   $$Q_{LB} = n(n+2) \sum_{k=1}^h \frac{\hat{\rho}^2(k)}{n-k}$$
>   Elle introduit le facteur correctif $\frac{n+2}{n-k} > 1$, qui accorde un poids plus important aux retards élevés $k$.
> 
> ---
> 
> **5. Choix pour $n$ petit ($n = 50$) :**
> - Le test de **Ljung-Box est nettement préférable**.
> - *Raison technique :* Pour des échantillons de petite taille ($n = 50$), la variance des estimateurs $\hat{\rho}(k)$ aux ordres élevés s'éloigne de $1/n$ et vaut approximativement $\frac{n-k}{n(n+2)}$. Le test de [[60.1.24. Test de Box - Pierce|Box-Pierce]] sous-estime systématiquement cette variance, conduisant à une statistique trop faible et un sous-rejet de l'hypothèse nulle (manque de puissance).
> - La statistique $Q_{LB}$ ajuste exactement cette variance pour que la distribution d'échantillon colle fidèlement à la loi théorique $\chi^2(h)$.

---

## Partie 5 : Code R

> [!question] Exercice 8 : Simulation et ACF
> Simuler un bruit blanc gaussien de $n = 200$ observations.
> 
> 1. Écrire le code R pour simuler la série.
> 2. Tracer la série et son ACF.
> 3. Que constatez-vous sur l'ACF ?
> 
> ```r
> # Code à compléter :
> set.seed(123)
> n <- 200
> X <- rnorm(...)
> plot(X, type = "l")
> acf(X, lag.max = 20)
> ```

> [!success] Correction détaillée : Exercice 8
> 
> **1 & 2. Code R complet :**
> ```r
> # 1. Simulation d'un bruit blanc gaussien standard
> set.seed(123)
> n <- 200
> X <- rnorm(n, mean = 0, sd = 1)
> 
> # 2. Tracé de la chronique temporelle et du corrélogramme
> par(mfrow = c(2, 1), mar = c(4, 4, 2, 1))
> plot(X, type = "l", col = "steelblue", lwd = 1.5,
>      main = "Simulation d'un bruit blanc gaussien (n = 200)",
>      xlab = "Temps t", ylab = expression(X[t]))
> abline(h = 0, col = "red", lty = 2)
> 
> acf(X, lag.max = 20, col = "darkblue", lwd = 2,
>     main = "ACF empirique du bruit blanc simulé")
> ```
> 
> **3. Constats sur le graphique de l'ACF :**
> - Au retard $h = 0$, $\hat{\rho}(0) = 1$ par définition.
> - Pour tous les retards $h \ge 1$, l'ensemble des bâtonnets se situe à l'intérieur des bandes de confiance en pointillés bleus tracées à $\pm 1.96 / \sqrt{200} \approx \pm 0.1386$.
> - Cela confirme l'absence d'autocorrélation sérielle : les tirages sont indépendants et identiquement distribués.

---

> [!question] Exercice 9 : Test de Ljung-Box avec R
> À partir de la série simulée dans l'exercice 8 :
> 
> 4. Appliquer le [[60.1.25. Test de Ljung - Box|test de Ljung-Box]] avec $h = 10$.
> 5. Interpréter la p-value obtenue.
> 
> ```r
> # Code à compléter :
> Box.test(X, lag = 10, type = ...)
> ```

> [!success] Correction détaillée : Exercice 9
> 
> **4. Code R complété :**
> ```r
> # Application du [[60.1.25. Test de Ljung - Box|test de Ljung-Box]] pour h = 10 retards
> test_lb <- Box.test(X, lag = 10, type = "Ljung-Box")
> print(test_lb)
> ```
> 
> **Résultat de la console R :**
> ```text
> 	Box-Ljung test
> 
> data:  X
> X-squared = 6.842, df = 10, p-value = 0.7403
> ```
> 
> **5. Interprétation statistique de la p-value :**
> - La statistique calculée vaut $Q_{obs} = 6.842$ pour un seuil critique $\chi_{10, 0.95}^2 \approx 18.31$.
> - La p-value est $p = 0.7403$, largement supérieure au seuil usuel $\alpha = 0.05$.
> - On **ne rejette pas l'hypothèse nulle $H_0$**.
> - Les données sont parfaitement compatibles avec un processus sans mémoire : la série simulée est bien un **bruit blanc**.
