z# TD-TP : Processus $AR(p)$ et $MA(q)$

## Partie 1 : Processus $AR(p)$

> [!question] Exercice 1 : $AR(1)$ - Calculs de base
> Soit $X_{t} = 0.7 X_{t-1} + \epsilon_{t}$ avec $\epsilon_{t} \sim BB(0, 4)$.
> 
> 1. Ce processus est-il stationnaire ? Justifier.
> 2. Calculer $\mathbb{E}[X_{t}]$.
> 3. Calculer $\gamma(0)$, $\gamma(1)$, $\gamma(2)$.
> 4. Calculer $\rho(1)$, $\rho(2)$.
> 
> *Indication : Utiliser $\gamma(0) = \sigma^{2} / (1 - \phi^{2})$ et $\gamma(h) = \phi^{h} \gamma(0)$.*

> [!note] Démonstration théorique : Justification des formules de $\gamma(0)$ et $\gamma(h)$ (Indications)
> 
> On considère un processus $\text{AR}(1)$ centré, stationnaire et causal :
> $$X_t = \phi X_{t-1} + \epsilon_t, \quad |\phi| < 1, \quad \epsilon_t \sim \text{BB}(0, \sigma^2)$$
> avec $\mathbb{E}[\epsilon_t] = 0$, $\operatorname{Var}(\epsilon_t) = \sigma^2$, et $\operatorname{Cov}(\epsilon_t, X_{t-h}) = 0$ pour tout $h \ge 1$ (le choc futur est indépendant des valeurs passées).
> 
> ---
> 
> **1. Démonstration de la récurrence $\gamma(h) = \phi^h \gamma(0)$ pour $h \ge 1$ :**
> Par définition de la fonction d'[[60.1.14. Fonction d'autocovariance théorique|autocovariance]] pour un processus centré ($\mu = 0$) :
> $$\gamma(h) = \operatorname{Cov}(X_t, X_{t-h}) = \mathbb{E}[X_t X_{t-h}]$$
> En remplaçant $X_t$ par son équation autorégressive $X_t = \phi X_{t-1} + \epsilon_t$ :
> $$\gamma(h) = \mathbb{E}[(\phi X_{t-1} + \epsilon_t) X_{t-h}] = \phi \mathbb{E}[X_{t-1} X_{t-h}] + \mathbb{E}[\epsilon_t X_{t-h}]$$
> 
> Or, par les propriétés structurelles du processus :
> - **Stationnarité :** $\mathbb{E}[X_{t-1} X_{t-h}] = \operatorname{Cov}(X_{t-1}, X_{t-h}) = \gamma((t-1) - (t-h)) = \gamma(h-1)$.
> - **Causalité :** Pour tout $h \ge 1$, la variable passée $X_{t-h}$ ne dépend que des chocs antérieurs $\{\epsilon_{t-h}, \epsilon_{t-h-1}, \dots\}$. Le choc présent $\epsilon_t$ est donc strictement orthogonal à $X_{t-h}$ :
>   $$\mathbb{E}[\epsilon_t X_{t-h}] = 0 \quad (\forall h \ge 1)$$
> 
> On obtient ainsi l'[[60.2.16. Équations de Yule - Walker|équation de Yule-Walker]] fondamentale au retard $h$ :
> $$\gamma(h) = \phi \gamma(h-1) \quad \forall h \ge 1$$
> 
> Par application successive de cette relation :
> - Pour $h = 1$ : $\gamma(1) = \phi \gamma(0)$
> - Pour $h = 2$ : $\gamma(2) = \phi \gamma(1) = \phi^2 \gamma(0)$
> - Par récurrence immédiate pour tout entier $h \ge 0$ :
>   $$\gamma(h) = \phi^h \gamma(0)$$
> *(Par parité $\gamma(-h) = \gamma(h)$, on a plus généralement $\gamma(h) = \phi^{|h|} \gamma(0)$ pour tout $h \in \mathbb{Z}$).*
> 
> ---
> 
> **2. Démonstration de la variance inconditionnelle $\gamma(0) = \frac{\sigma^2}{1 - \phi^2}$ :**
> 
> * **Méthode 1 — Par l'équation de variance (Yule-Walker pour $h=0$) :**
>   Prenons la variance des deux membres dans $X_t = \phi X_{t-1} + \epsilon_t$.
>   Comme $\operatorname{Cov}(X_{t-1}, \epsilon_t) = 0$ par causalité :
>   $$\operatorname{Var}(X_t) = \operatorname{Var}(\phi X_{t-1} + \epsilon_t) = \phi^2 \operatorname{Var}(X_{t-1}) + \operatorname{Var}(\epsilon_t)$$
>   Par stationnarité faible, $\operatorname{Var}(X_t) = \operatorname{Var}(X_{t-1}) = \gamma(0)$, et $\operatorname{Var}(\epsilon_t) = \sigma^2$ :
>   $$\gamma(0) = \phi^2 \gamma(0) + \sigma^2$$
>   $$\gamma(0)(1 - \phi^2) = \sigma^2$$
>   Puisque le processus est stationnaire ($|\phi| < 1 \implies 1 - \phi^2 > 0$), on obtient :
>   $$\gamma(0) = \frac{\sigma^2}{1 - \phi^2}$$
> 
> * **Méthode 2 — Par la [[60.2.9. Représentation MA infini de l'AR(1)|représentation MA(∞)]] (Wold) :**
>   En substituant récursivement le passé dans $X_t = \phi X_{t-1} + \epsilon_t$ :
>   $$X_t = \epsilon_t + \phi \epsilon_{t-1} + \phi^2 \epsilon_{t-2} + \dots = \sum_{j=0}^{+\infty} \phi^j \epsilon_{t-j}$$
>   Les innovations $\epsilon_{t-j}$ étant décorrélées et de variance $\sigma^2$ :
>   $$\gamma(0) = \operatorname{Var}(X_t) = \sum_{j=0}^{+\infty} \operatorname{Var}(\phi^j \epsilon_{t-j}) = \sigma^2 \sum_{j=0}^{+\infty} (\phi^2)^j$$
>   Comme $|\phi| < 1$, la série géométrique converge vers $\frac{1}{1 - \phi^2}$, d'où :
>   $$\gamma(0) = \frac{\sigma^2}{1 - \phi^2}$$

> [!success] Première méthode : Utilisation directe des formules de l'énoncé (Méthode rapide)
> 
> Ici $\phi = 0.7$, la constante est $c = 0$, et la variance du bruit est $\sigma^2 = 4$.
> 
> **1. Condition de stationnarité :**
> - D'après la [[60.2.8. Condition de stationnarité de l'AR(1)|condition de stationnarité de l'AR(1)]], le polynôme caractéristique associé est $\Phi(z) = 1 - 0.7 z$.
> - Sa racine est $z_0 = \frac{1}{0.7} = \frac{10}{7} \approx 1.4286$.
> - Comme $|z_0| > 1$ (ou de façon équivalente $|\phi| = 0.7 < 1$), la racine est strictement à l'extérieur du disque unité fermé.
> **Conclusion :** Le processus est **stationnaire au sens faible** et causal.
> 
> ---
> 
> **2. Espérance mathématique $\mathbb{E}[X_t]$ :**
> - Le processus étant centré (aucune constante ajoutée, $c = 0$), par passage à l'espérance dans $X_t = 0.7 X_{t-1} + \epsilon_t$ sous hypothèse de stationnarité :
>   $$\mathbb{E}[X_t] = 0.7 \mathbb{E}[X_{t-1}] + \mathbb{E}[\epsilon_t] \implies \mu = 0.7 \mu + 0 \implies (1 - 0.7)\mu = 0 \implies \mu = 0$$
>   Donc $\mathbb{E}[X_t] = 0$.
> 
> ---
> 
> **3. Calcul des autocovariances $\gamma(0), \gamma(1), \gamma(2)$ :**
> - **Variance $\gamma(0)$ :**
>   $$\gamma(0) = \frac{\sigma^2}{1 - \phi^2} = \frac{4}{1 - 0.7^2} = \frac{4}{1 - 0.49} = \frac{4}{0.51} = \frac{400}{51} \approx 7.8431$$
> 
> - **Autocovariance d'ordre 1 $\gamma(1)$ :**
>   $$\gamma(1) = \phi \gamma(0) = 0.7 \times \frac{400}{51} = \frac{280}{51} \approx 5.4902$$
> 
> - **Autocovariance d'ordre 2 $\gamma(2)$ :**
>   $$\gamma(2) = \phi^2 \gamma(0) = 0.49 \times \frac{400}{51} = \frac{196}{51} \approx 3.8431$$
> 
> ---
> 
> **4. Calcul des autocorrélations $\rho(1), \rho(2)$ :**
> - Par définition, $\rho(h) = \frac{\gamma(h)}{\gamma(0)} = \phi^h$ :
>   $$\rho(1) = \phi^1 = 0.70$$
>   $$\rho(2) = \phi^2 = 0.7^2 = 0.49$$

---

> [!success] Deuxième méthode de correction : Calcul direct par les covariances (sans les formules de l'énoncé)
> 
> Dans cette approche, **on n'utilise aucune formule préétablie** (ni $\gamma(0) = \frac{\sigma^2}{1-\phi^2}$, ni $\gamma(h) = \phi^h \gamma(0)$). On calcule tout pas à pas à partir de la définition de la covariance et de l'équation du modèle :
> $$X_t = 0.7 X_{t-1} + \epsilon_t \quad \text{avec} \quad \epsilon_t \sim \text{BB}(0, 4)$$
> 
> ---
> 
> **1. Condition de stationnarité :**
> - Le polynôme caractéristique associé au retard est $\Phi(z) = 1 - 0.7 z$.
> - Sa racine vaut $z_0 = \frac{1}{0.7} = \frac{10}{7} \approx 1.4286 > 1$.
> - Comme la racine est strictement à l'extérieur du disque unité fermé (ou $|0.7| < 1$), le processus est **stationnaire au sens faible** et causal.
> 
> ---
> 
> **2. Espérance mathématique $\mathbb{E}[X_t]$ :**
> - Par stationnarité, la moyenne est constante : $\mathbb{E}[X_t] = \mathbb{E}[X_{t-1}] = \mu$.
> - En prenant l'espérance des deux côtés de $X_t = 0.7 X_{t-1} + \epsilon_t$ :
>   $$\mathbb{E}[X_t] = 0.7 \mathbb{E}[X_{t-1}] + \mathbb{E}[\epsilon_t] \implies \mu = 0.7 \mu + 0 \implies 0.3 \mu = 0 \implies \mu = 0$$
> - Le processus est donc strictement centré.
> 
> ---
> 
> **3. Calcul direct des covariances $\gamma(0), \gamma(1), \gamma(2)$ :**
> 
> Oublie cette étape, il y a beaucoup plus simple en utilisant directement la **variance** au lieu de développer le produit.
> 
> On part de l'équation de base :
> 
> $$X_t = 0{,}7 X_{t-1} + \epsilon_t$$
> 
> Par définition, $\gamma(0) = \mathbb{V}(X_t)$. On applique donc la variance des deux côtés :
> 
> $$\mathbb{V}(X_t) = \mathbb{V}(0{,}7 X_{t-1} + \epsilon_t)$$
> 
> Deux règles de base sur la variance :
> 
> 1. $\mathbb{V}(aY) = a^2 \mathbb{V}(Y)$ (le coefficient sort au carré).
> 2. Pour deux variables indépendantes, $\mathbb{V}(A + B) = \mathbb{V}(A) + \mathbb{V}(B)$.
> 
> Comme le choc $\epsilon_t$ survient à l'instant $t$, il est indépendant de la valeur passée $X_{t-1}$. On peut donc séparer la variance :
> 
> $$\mathbb{V}(X_t) = 0{,}7^2 \mathbb{V}(X_{t-1}) + \mathbb{V}(\epsilon_t)$$
> 
> Comme le processus est stationnaire, la variance est la même à tout instant : $\mathbb{V}(X_t) = \mathbb{V}(X_{t-1}) = \gamma(0)$. Et l'énoncé donne $\mathbb{V}(\epsilon_t) = 4$.
> 
> L'équation devient :
> 
> $$\gamma(0) = 0{,}49 \gamma(0) + 4$$
> 
> On isole $\gamma(0)$ :
> 
> $$\gamma(0) - 0{,}49 \gamma(0) = 4$$
> 
> $$0{,}51 \gamma(0) = 4$$
> 
> $$\gamma(0) = \frac{4}{0{,}51} = \frac{400}{51} \approx 7{,}84$$
> 
> ---
> 
> Pour $\gamma(1)$, on applique la formule de la covariance entre $X_t$ et $X_{t-1}$ :
> 
> $$\gamma(1) = \text{Cov}(X_t, X_{t-1})$$
> 
> On remplace $X_t$ par son expression ($0{,}7 X_{t-1} + \epsilon_t$) :
> 
> $$\gamma(1) = \text{Cov}(0{,}7 X_{t-1} + \epsilon_t, X_{t-1})$$
> 
> On sépare grâce à la bilinéarité de la covariance :
> 
> $$\gamma(1) = 0{,}7 \underbrace{\text{Cov}(X_{t-1}, X_{t-1})}_{=\mathbb{V}(X_{t-1}) = \gamma(0)} + \underbrace{\text{Cov}(\epsilon_t, X_{t-1})}_{= 0 \text{ car indépendants}}$$
> 
> Ce qui donne directement :
> 
> $$\gamma(1) = 0{,}7 \gamma(0) = 0{,}7 \times \frac{400}{51} = \frac{280}{51} \approx 5{,}49$$
> 
> Même logique pour $\gamma(2)$ :
> 
> $$\gamma(2) = \text{Cov}(X_t, X_{t-2}) = 0{,}7 \text{Cov}(X_{t-1}, X_{t-2}) = 0{,}7 \gamma(1) = 0{,}7 \times \frac{280}{51} = \frac{196}{51} \approx 3{,}84$$
> 
> ---
> 
> **4. Calcul direct des autocorrélations $\rho(1)$ et $\rho(2)$ :**
> Par définition du coefficient de corrélation linéaire $\rho(h) = \frac{\operatorname{Cov}(X_t, X_{t-h})}{\sqrt{\operatorname{Var}(X_t)\operatorname{Var}(X_{t-h})}} = \frac{\gamma(h)}{\gamma(0)}$ :
> - **Pour $h = 1$ :**
>   $$\rho(1) = \frac{\gamma(1)}{\gamma(0)} = \frac{0.7 \gamma(0)}{\gamma(0)} = 0.70 = \frac{280/51}{400/51} = \frac{280}{400}$$
> - **Pour $h = 2$ :**
>   $$\rho(2) = \frac{\gamma(2)}{\gamma(0)} = \frac{0.7 \gamma(1)}{\gamma(0)} = \frac{0.7 \times 0.7 \gamma(0)}{\gamma(0)} = 0.7^2 = 0.49 = \frac{196/51}{400/51} = \frac{196}{400}$$

---

> [!question] Exercice 2 : $AR(2)$ - Vérification de stationnarité
> On considère les processus $AR(2)$ suivants :
> - (a) $X_{t} = 0.8 X_{t-1} + 0.1 X_{t-2} + \epsilon_{t}$
> - (b) $X_{t} = 1.2 X_{t-1} - 0.6 X_{t-2} + \epsilon_{t}$
> - (c) $X_{t} = 0.5 X_{t-1} + 0.8 X_{t-2} + \epsilon_{t}$
> 
> Pour chaque processus, déterminer s'il est stationnaire. Justifier.
> 
> *Indication : Utiliser les conditions $|\phi_{2}| < 1$, $\phi_{2} + \phi_{1} < 1$, $\phi_{2} - \phi_{1} < 1$.*

> [!success] Correction détaillée : Exercice 2
> 
> Pour un processus $AR(2) : X_t = \phi_1 X_{t-1} + \phi_2 X_{t-2} + \epsilon_t$, les conditions nécessaires et suffisantes de stationnarité ([[60.2.19. Cas particulier de l'AR(2) et triangle de stationnarité|triangle de stationnarité]]) sont :
> 1. $|\phi_2| < 1$
> 2. $\phi_2 + \phi_1 < 1$
> 3. $\phi_2 - \phi_1 < 1$
> 
> ---
> 
> **Processus (a) : $\phi_1 = 0.8, \phi_2 = 0.1$**
> - Condition 1 : $|\phi_2| = |0.1| = 0.1 < 1$ (Vérifiée)
> - Condition 2 : $\phi_2 + \phi_1 = 0.1 + 0.8 = 0.9 < 1$ (Vérifiée)
> - Condition 3 : $\phi_2 - \phi_1 = 0.1 - 0.8 = -0.7 < 1$ (Vérifiée)
> 
> **Conclusion (a) :** Le processus est **stationnaire**.
> 
> ---
> 
> **Processus (b) : $\phi_1 = 1.2, \phi_2 = -0.6$**
> - Condition 1 : $|\phi_2| = |-0.6| = 0.6 < 1$ (Vérifiée)
> - Condition 2 : $\phi_2 + \phi_1 = -0.6 + 1.2 = 0.6 < 1$ (Vérifiée)
> - Condition 3 : $\phi_2 - \phi_1 = -0.6 - 1.2 = -1.8 < 1$ (Vérifiée)
> 
> **Conclusion (b) :** Le processus est **stationnaire** *(Note : Le discriminant $\Delta = 1.2^2 - 4(0.6) = 1.44 - 2.40 = -0.96 < 0$ indique des racines complexes conjuguées de module $1/\sqrt{0.6} \approx 1.29 > 1$, induisant des oscillations amorties)*.
> 
> ---
> 
> **Processus (c) : $\phi_1 = 0.5, \phi_2 = 0.8$**
> - Condition 1 : $|\phi_2| = |0.8| = 0.8 < 1$ (Vérifiée)
> - Condition 2 : $\phi_2 + \phi_1 = 0.8 + 0.5 = 1.3 \not< 1$ (**Violée car $1.3 > 1$**)
> 
> **Conclusion (c) :** Le processus est **non stationnaire** *(le polynôme admet au moins une racine à l'intérieur du cercle unité)*.

---

> [!question] Exercice 3 : $AR(1)$ vs $AR(2)$ - Identification
> On observe les PACF suivantes pour deux séries :
> - **Série A** : PACF nulle après $h=1$.
> - **Série B** : PACF nulle après $h=2$.
> 
> 1. Quel type de modèle est le plus probable pour chaque série ?
> 2. Justifier votre réponse.

> [!success] Correction détaillée : Exercice 3
> 
> **1. Modèles identifiés :**
> - **Série A :** Modèle **$\text{AR}(1)$**.
> - **Série B :** Modèle **$\text{AR}(2)$**.
> 
> ---
> 
> **2. Justification théorique (Théorème de coupure de la PACF) :**
> - Par définition, le coefficient d'autocorrélation partielle $\alpha(h)$ mesure la corrélation linéaire résiduelle entre $X_t$ et $X_{t-h}$ après avoir retiré l'influence linéaire des retards intermédiaires $X_{t-1}, \dots, X_{t-h+1}$.
> - Pour tout processus autorégressif $\text{AR}(p)$ stationnaire, la théorie démontre que :
>   $$\alpha(p) = \phi_p \ne 0$$
>   $$\alpha(h) = 0 \quad \forall h > p$$
> - **Application :**
>   - Pour la **Série A**, la PACF se coupe nettement dès le retard $h = 1$ (seul $\hat{\alpha}(1) \ne 0$). C'est la signature exclusive d'un processus **$\text{AR}(1)$**.
>   - Pour la **Série B**, la coupure franche s'opère strictement après $h = 2$ ($\\hat{\alpha}(1) \ne 0$ et $\hat{\alpha}(2) \ne 0$, puis $\hat{\alpha}(h) \approx 0$ pour tout $h \ge 3$). C'est la signature exclusive d'un processus **$\text{AR}(2)$**.

---

> [!question] Exercice 4 : Simulation $AR(1)$
> On souhaite simuler un $AR(1)$ avec $\phi = 0.8$ et $\sigma^{2} = 1$.
> 
> 1. Écrire le code R pour simuler $n = 200$ observations.
> 2. Tracer l'ACF et la PACF empiriques.
> 
> ```r
> # Code R à compléter :
> set.seed(123)
> n <- 200
> phi <- 0.8
> sigma <- 1
> X <- arima.sim(...) # à compléter
> par(mfrow = c(1, 2))
> acf(X, lag.max = 20)
> pacf(X, lag.max = 20)
> ```

> [!success] Correction détaillée : Exercice 4
> 
> **1 & 2. Code R complet :**
> ```r
> # Initialisation
> set.seed(123)
> n <- 200
> phi <- 0.8
> sigma <- 1
> 
> # 1. Simulation avec arima.sim
> X <- arima.sim(model = list(ar = phi), n = n, sd = sigma)
> 
> # 2. Tracé de l'ACF et de la PACF
> par(mfrow = c(1, 2), mar = c(4, 4, 2, 1))
> acf(X, lag.max = 20, col = "steelblue", lwd = 2,
>     main = "ACF empirique AR(1)")
> pacf(X, lag.max = 20, col = "darkred", lwd = 2,
>      main = "PACF empirique AR(1)")
> ```
> 
> **Commentaire sur les graphiques obtenus :**
> - **ACF empirique :** Décroissance exponentielle régulière vers zéro, caractéristique des puissances $\rho(h) = 0.8^h$.
> - **PACF empirique :** Un pic positif net et significatif au retard $h = 1$ ($\\hat{\alpha}(1) \approx 0.8$), puis tous les coefficients pour $h \ge 2$ sont inclus dans la bande de confiance $\pm 1.96 / \sqrt{200} \approx \pm 0.1386$.

---

> [!question] Exercice 5 : Simulation $AR(2)$
> On souhaite simuler un $AR(2)$ avec $\phi_{1} = 0.5$, $\phi_{2} = -0.2$ et $\sigma^{2} = 1$.
> 
> 1. Écrire le code R pour simuler $n = 200$ observations.
> 2. Tracer l'ACF et la PACF empiriques.
> 3. Interpréter les graphiques obtenus.
> 
> ```r
> # Code R à compléter :
> set.seed(123)
> n <- 200
> X <- arima.sim(...) # à compléter
> par(mfrow = c(1, 2))
> acf(X, lag.max = 10)
> pacf(X, lag.max = 10)
> ```

> [!success] Correction détaillée : Exercice 5
> 
> **1 & 2. Code R complété :**
> ```r
> set.seed(123)
> n <- 200
> 
> # Simulation d'un AR(2)
> X <- arima.sim(model = list(ar = c(0.5, -0.2)), n = n, sd = 1)
> 
> # Visualisation conjointe ACF / PACF
> par(mfrow = c(1, 2), mar = c(4, 4, 2, 1))
> acf(X, lag.max = 10, col = "steelblue", lwd = 2,
>     main = "ACF empirique AR(2)")
> pacf(X, lag.max = 10, col = "darkred", lwd = 2,
>      main = "PACF empirique AR(2)")
> ```
> 
> **3. Interprétation des graphiques :**
> - **ACF empirique :** Elle décroît vers zéro de façon pseudo-sinusoïdale amortie sous l'effet conjugué des deux coefficients autorégressifs.
> - **PACF empirique :** Elle présente **exactement deux bâtonnets significatifs** :
>   - un pic positif au retard $h = 1$,
>   - un pic négatif significatif au retard $h = 2$ ($\\hat{\alpha}(2) \approx \phi_2 = -0.2$).
>   - Dès le retard $h = 3$, les bâtonnets tombent sous le seuil critique de Bartlett et ne sont plus significativement différents de 0.
> - Cette coupure nette à l'ordre 2 confirme visuellement et empiriquement l'ordre autorégressif $p = 2$.

---

> [!question] Exercice 6 : Équations de Yule-Walker
> Pour un $AR(2)$ stationnaire, on observe $\rho(1) = 0.6$ et $\rho(2) = 0.2$.
> 
> 4. Écrire les équations de Yule-Walker pour $h=1$ et $h=2$.
> 5. En déduire les coefficients $\phi_{1}$ et $\phi_{2}$.
> 
> *Indication : Résoudre le système $\rho(1) = \phi_{1} + \phi_{2}\rho(1)$ et $\rho(2) = \phi_{1}\rho(1) + \phi_{2}$.*

> [!success] Correction détaillée : Exercice 6
> 
> **4. [[60.2.16. Équations de Yule - Walker|Système de Yule-Walker]] (voir la [[60.2.16. Équations de Yule - Walker|forme matricielle]] et la [[60.2.16.1. Exemple AR(2) sous Yule - Walker|résolution de l'AR(2)]]) :**
> Pour un $AR(2)$ centré stationnaire $X_t = \phi_1 X_{t-1} + \phi_2 X_{t-2} + \epsilon_t$, en multipliant par $X_{t-h}$ et en prenant l'espérance mathématique, on obtient le système :
> - Pour $h = 1$ :
>   $$\rho(1) = \phi_1 + \phi_2 \rho(1)$$
> - Pour $h = 2$ :
>   $$\rho(2) = \phi_1 \rho(1) + \phi_2$$
> 
> En remplaçant par les valeurs numériques $\rho(1) = 0.6$ et $\rho(2) = 0.2$ :
> $$\begin{cases} 0.6 = \phi_1 + 0.6 \phi_2 \\ 0.2 = 0.6 \phi_1 + \phi_2 \end{cases}$$
> 
> ---
> 
> **5. Résolution du système :**
> - De la première équation :
>   $$\phi_1 = 0.6 - 0.6 \phi_2 = 0.6(1 - \phi_2)$$
> 
> - On injecte cette expression dans la seconde équation :
>   $$0.2 = 0.6[0.6(1 - \phi_2)] + \phi_2$$
>   $$0.2 = 0.36(1 - \phi_2) + \phi_2$$
>   $$0.2 = 0.36 - 0.36 \phi_2 + \phi_2$$
>   $$0.2 - 0.36 = 0.64 \phi_2$$
>   $$-0.16 = 0.64 \phi_2 \implies \phi_2 = -\frac{0.16}{0.64} = -0.25$$
> 
> - On en déduit alors $\phi_1$ :
>   $$\phi_1 = 0.6 - 0.6(-0.25) = 0.6 + 0.15 = 0.75$$
> 
> **Vérification de la stationnarité :**
> - $|\phi_2| = |-0.25| = 0.25 < 1$
> - $\phi_2 + \phi_1 = -0.25 + 0.75 = 0.50 < 1$
> - $\phi_2 - \phi_1 = -0.25 - 0.75 = -1.00 < 1$
> 
> **Conclusion :** Les coefficients sont **$\phi_1 = 0.75$** et **$\phi_2 = -0.25$**.

---

## Partie 2 : Processus $MA(q)$

> [!question] Exercice 7 : $MA(1)$ - Calculs de base
> Soit $X_{t} = \epsilon_{t} + 0.6 \epsilon_{t-1}$ avec $\epsilon_{t} \sim BB(0, 4)$.
> 
> 1. Ce processus est-il stationnaire ? Justifier.
> 2. Calculer $\mathbb{E}[X_{t}]$.
> 3. Calculer $\gamma(0)$, $\gamma(1)$, $\gamma(2)$.
> 4. Calculer $\rho(1)$, $\rho(2)$.
> 5. Vérifier que $|\rho(1)| \le 0.5$.
> 
> *Indication : $\rho(1) = \frac{\theta}{1 + \theta^{2}}$.*

> [!success] Correction détaillée : Exercice 7
> 
> Ici $\theta = 0.6$ et $\sigma^2 = 4$.
> 
> **1. Stationnarité :**
> - Tout processus moyenne mobile d'ordre fini $MA(q)$ est une somme finie de variables aléatoires non corrélées d'espérances nulles et de variances finies.
> - **Conclusion :** Le processus est **toujours stationnaire au sens faible**, indépendamment de la valeur de $\theta$.
> 
> ---
> 
> **2. Espérance mathématique $\mathbb{E}[X_t]$ :**
> - $\mathbb{E}[X_t] = \mathbb{E}[\epsilon_t] + 0.6 \mathbb{E}[\epsilon_{t-1}] = 0 + 0 = 0$.
> 
> ---
> 
> **3. Calcul des autocovariances $\gamma(0), \gamma(1), \gamma(2)$ :**
> - **Variance $\gamma(0)$ :**
>   $$\gamma(0) = \operatorname{Var}(\epsilon_t + 0.6 \epsilon_{t-1}) = \sigma^2(1 + \theta^2) = 4(1 + 0.6^2) = 4 \times 1.36 = 5.44$$
> 
> - **Autocovariance d'ordre 1 $\gamma(1)$ :**
>   $$\gamma(1) = \operatorname{Cov}(\epsilon_t + 0.6 \epsilon_{t-1}, \epsilon_{t-1} + 0.6 \epsilon_{t-2}) = 0.6 \operatorname{Var}(\epsilon_{t-1}) = 0.6 \times 4 = 2.40$$
> 
> - **Autocovariance d'ordre 2 $\gamma(2)$ :**
>   $$\gamma(2) = 0 \quad (\text{car } h = 2 > q = 1)$$
> 
> ---
> 
> **4. Autocorrélations $\rho(1), \rho(2)$ :**
> - $\rho(1) = \frac{\gamma(1)}{\gamma(0)} = \frac{\theta}{1 + \theta^2} = \frac{0.6}{1 + 0.36} = \frac{0.6}{1.36} = \frac{15}{34} \approx 0.4412$
> - $\rho(2) = \frac{\gamma(2)}{\gamma(0)} = 0$
> 
> ---
> 
> **5. Vérification de la borne $|\rho(1)| \le 0.5$ :**
> - Numériquement : $|\rho(1)| = 0.4412 \le 0.5$.
> - Démonstration théorique générale :
>   $$(1 - |\theta|)^2 \ge 0 \iff 1 + \theta^2 - 2|\theta| \ge 0 \iff 1 + \theta^2 \ge 2|\theta|$$
>   En divisant par $1 + \theta^2 > 0$ :
>   $$|\rho(1)| = \frac{|\theta|}{1 + \theta^2} \le \frac{1}{2} = 0.5$$
>   Le maximum $|\rho(1)| = 0.5$ est atteint si et seulement si $|\theta| = 1$.

---

> [!question] Exercice 8 : $MA(2)$ - Conditions d'inversibilité
> On considère les processus $MA(2)$ suivants :
> - (a) $X_{t} = \epsilon_{t} + 0.8 \epsilon_{t-1} + 0.6 \epsilon_{t-2}$
> - (b) $X_{t} = \epsilon_{t} - 0.5 \epsilon_{t-1} + 0.9 \epsilon_{t-2}$
> - (c) $X_{t} = \epsilon_{t} + 1.2 \epsilon_{t-1} - 0.8 \epsilon_{t-2}$
> 
> Pour chaque processus, déterminer s'il est [[60.2.22. Condition d'inversibilité du MA(q)|inversible]]. Justifier.
> 
> *Indication : Résoudre $\Theta(z) = 0$ et vérifier $|z| > 1$, ou utiliser les conditions du [[60.2.26. Cas particulier du MA(2)|triangle d'inversibilité du MA(2)]] par [[60.2.27. Dualité AR(p) et MA(q)|dualité]] avec l'$AR(2)$.*

> [!success] Correction détaillée : Exercice 8
> 
> Le polynôme de moyenne mobile associé à $X_t = \epsilon_t + \theta_1 \epsilon_{t-1} + \theta_2 \epsilon_{t-2}$ est :
> $$\Theta(z) = 1 + \theta_1 z + \theta_2 z^2$$
> Le processus est [[60.2.22. Condition d'inversibilité du MA(q)|inversible]] si et seulement si toutes les racines de $\Theta(z) = 0$ sont de module strictement supérieur à 1 ($|z_i| > 1$). Par [[60.2.27. Dualité AR(p) et MA(q)|dualité]] avec l'$AR(2)$ (voir [[60.2.26. Cas particulier du MA(2)|Cas particulier du MA(2)]] et le [[60.2.19. Cas particulier de l'AR(2) et triangle de stationnarité|triangle de stationnarité]]), cela équivaut aux trois conditions sur les coefficients (triangle d'inversibilité) :
> 1. $|\theta_2| < 1$
> 2. $1 + \theta_1 + \theta_2 > 0$
> 3. $1 - \theta_1 + \theta_2 > 0$
> 
> ---
> 
> **Processus (a) : $\theta_1 = 0.8, \theta_2 = 0.6$**
> - $|\theta_2| = 0.6 < 1$ (Vrai)
> - $1 + \theta_1 + \theta_2 = 1 + 0.8 + 0.6 = 2.4 > 0$ (Vrai)
> - $1 - \theta_1 + \theta_2 = 1 - 0.8 + 0.6 = 0.8 > 0$ (Vrai)
> 
> **Conclusion (a) :** Le processus est **[[60.2.22. Condition d'inversibilité du MA(q)|inversible]]**.
> 
> ---
> 
> **Processus (b) : $\theta_1 = -0.5, \theta_2 = 0.9$**
> - $|\theta_2| = 0.9 < 1$ (Vrai)
> - $1 + \theta_1 + \theta_2 = 1 - 0.5 + 0.9 = 1.4 > 0$ (Vrai)
> - $1 - \theta_1 + \theta_2 = 1 - (-0.5) + 0.9 = 2.4 > 0$ (Vrai)
> 
> **Conclusion (b) :** Le processus est **[[60.2.22. Condition d'inversibilité du MA(q)|inversible]]**.
> 
> ---
> 
> **Processus (c) : $\theta_1 = 1.2, \theta_2 = -0.8$**
> - $|\theta_2| = |-0.8| = 0.8 < 1$ (Vrai)
> - $1 + \theta_1 + \theta_2 = 1 + 1.2 - 0.8 = 1.4 > 0$ (Vrai)
> - $1 - \theta_1 + \theta_2 = 1 - 1.2 - 0.8 = -1.0 \not> 0$ (**Faux car $-1.0 < 0$**)
> 
> **Conclusion (c) :** Le processus est **non [[60.2.22. Condition d'inversibilité du MA(q)|inversible]]** *(l'une des racines se situe à l'intérieur du disque unité : les racines réelles sont $z_1 \approx 0.596$ avec $|z_1| < 1$ et $z_2 \approx -2.096$)*.

---

> [!question] Exercice 9 : $MA(1)$ vs $MA(2)$ - Identification
> On observe les ACF suivantes pour deux séries :
> - **Série A** : ACF nulle après $h=1$.
> - **Série B** : ACF nulle après $h=2$.
> 
> 1. Quel type de modèle est le plus probable pour chaque série ?
> 2. Justifier votre réponse.

> [!success] Correction détaillée : Exercice 9
> 
> **1. Modèles identifiés :**
> - **Série A :** Modèle **$\text{MA}(1)$**.
> - **Série B :** Modèle **$\text{MA}(2)$**.
> 
> ---
> 
> **2. Justification théorique :**
> - La fonction d'autocorrélation $\rho(h)$ d'un processus à moyenne mobile $\text{MA}(q)$ possède la propriété remarquable de s'annuler strictement au-delà de l'ordre $q$ :
>   $$\rho(q) \ne 0$$
>   $$\rho(h) = 0 \quad \forall h > q$$
> - **Pour la Série A :** L'ACF s'annule immédiatement après $h = 1$ (seul $\rho(1)$ est non nul). Cela correspond précisément à l'empreinte d'un processus **$\text{MA}(1)$**.
> - **Pour la Série B :** L'ACF présente deux retards non nuls $\rho(1) \ne 0$ et $\rho(2) \ne 0$, puis tombe strictement à 0 pour tout $h \ge 3$. Cela correspond à la signature d'un processus **$\text{MA}(2)$**.

---

> [!question] Exercice 10 : Simulation $MA(1)$
> On souhaite simuler un $MA(1)$ avec $\theta = 0.8$ et $\sigma^{2} = 1$.
> 
> 1. Écrire le code R pour simuler $n = 200$ observations.
> 2. Tracer l'ACF empirique.
> 
> ```r
> # Code R à compléter :
> set.seed(123)
> n <- 200
> theta <- 0.8
> sigma <- 1
> X <- arima.sim(...) # à compléter
> acf(X, lag.max = 20)
> ```

> [!success] Correction détaillée : Exercice 10
> 
> **1 & 2. Code R complet :**
> ```r
> set.seed(123)
> n <- 200
> theta <- 0.8
> sigma <- 1
> 
> # Simulation d'un MA(1)
> X <- arima.sim(model = list(ma = theta), n = n, sd = sigma)
> 
> # Tracé de l'ACF empirique
> acf(X, lag.max = 20, col = "steelblue", lwd = 2,
>     main = "ACF empirique d'un MA(1)")
> ```
> 
> **Commentaire sur le résultat obtenu :**
> - On observe un pic d'autocorrélation positif très marqué au premier retard :
>   $$\hat{\rho}(1) \approx \frac{0.8}{1 + 0.8^2} = \frac{0.8}{1.64} \approx 0.4878$$
> - Dès le retard $h = 2$ et pour tous les retards suivants jusqu'à 20, les coefficients restent tous enfermés à l'intérieur des bandes de confiance en pointillés $\pm 1.96 / \sqrt{200} \approx \pm 0.1386$.
> - Le graphique valide empiriquement la coupure franche à $q = 1$.

---

> [!question] Exercice 11 : Simulation $MA(2)$
> On souhaite simuler un $MA(2)$ avec $\theta_{1} = 0.7$, $\theta_{2} = -0.9$ et $\sigma^{2} = 1$.
> 
> 1. Écrire le code R pour simuler $n = 200$ observations.
> 2. Tracer l'ACF empirique.
> 3. Interpréter les graphiques obtenus.
> 
> ```r
> # Code R à compléter :
> set.seed(123)
> n <- 200
> X <- arima.sim(...) # à compléter
> acf(X, lag.max = 20)
> ```

> [!success] Correction détaillée : Exercice 11
> 
> **1 & 2. Code R complété :**
> ```r
> set.seed(123)
> n <- 200
> 
> # Simulation du MA(2)
> X <- arima.sim(model = list(ma = c(0.7, -0.9)), n = n, sd = 1)
> 
> # Visualisation de l'ACF empirique
> acf(X, lag.max = 20, col = "steelblue", lwd = 2,
>     main = "ACF empirique d'un MA(2)")
> ```
> 
> **3. Interprétation statistique du graphique :**
> - **Au retard $h = 1$ :** Présence d'un pic d'autocorrélation positif significatif (dû au produit croisé $\theta_1 + \theta_1 \theta_2$).
> - **Au retard $h = 2$ :** Présence d'un pic négatif très prononcé qui franchit nettement la bande de confiance inférieure (reflétant la valeur $\theta_2 = -0.9$).
> - **Pour les retards $h \ge 3$ :** L'ACF tombe brutalement à zéro et aucun bâtonnet ne dépasse significativement des bandes de confiance de Bartlett.
> - **Conclusion :** Ce profil correspond exactement à la signature théorique d'un modèle $\text{MA}(2)$, caractérisé par une coupure nette après l'ordre $q = 2$.
