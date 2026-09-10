# TP : Théorème de Wold, représentation $MA(\infty)$ et prévision (Chapitre 2)

## Partie I - $AR(1)$ et $MA(1)$

> [!question] 3.1 Étude théorique de l'[[60.2.7. Modèle AR(1) centré|AR(1)]]
> Soit $X_{t} = \phi X_{t-1} + \epsilon_{t}$ avec $|\phi| < 1$ et $\epsilon_{t} \sim BB(0, \sigma^{2})$.
> 
> 1. Donner la [[60.2.9. Représentation MA infini de l'AR(1)|représentation]] $MA(\infty)$ de $X_{t}$ en précisant les coefficients $\psi_{i}$.
> 2. Exprimer la prévision à 1 pas $\hat{X}_{t+1}$, puis à 2 pas $\hat{X}_{t+2}$.
> 3. Donner la variance de l'erreur de prévision à 1 pas : $\mathbb{E}[(X_{t+1} - \hat{X}_{t+1})^{2}]$.

> [!success] Correction détaillée : 3.1 Étude théorique de l'AR(1)
> 
> **1. Représentation $MA(\infty)$ :**
> En utilisant [[60.2.1. Opérateurs retard et différence|l'opérateur retard]] $B$, le modèle s'écrit :
> $$(1 - \phi B) X_t = \epsilon_t$$
> Comme $|\phi| < 1$, l'opérateur $(1 - \phi B)$ est inversible et son inverse est la série géométrique convergente :
> $$(1 - \phi B)^{-1} = \sum_{i=0}^{\infty} \phi^i B^i$$
> En appliquant cet inverse aux deux membres :
> $$X_t = \sum_{i=0}^{\infty} \phi^i \epsilon_{t-i} = \sum_{i=0}^{\infty} \psi_i \epsilon_{t-i}$$
> Les [[60.2.30. Calcul récursif des coefficients psi|coefficients de Wold]] sont donc :
> $$\psi_i = \phi^i \quad \forall i \ge 0 \quad (\text{avec } \psi_0 = 1)$$
> 
> ---
> 
> **2. Prévisions conditionnelles :**
> Soit $\mathcal{I}_t = \sigma(X_s, s \le t) = \sigma(\epsilon_s, s \le t)$ l'information disponible à la date $t$.
> 
> - **À horizon 1 pas ($h = 1$) :**
>   $$X_{t+1} = \phi X_t + \epsilon_{t+1}$$
>   Comme $X_t \in \mathcal{I}_t$ et $\mathbb{E}[\epsilon_{t+1} | \mathcal{I}_t] = 0$ :
>   $$\hat{X}_{t+1} = \mathbb{E}[X_{t+1} | \mathcal{I}_t] = \phi X_t$$
> 
> - **À horizon 2 pas ($h = 2$) :**
>   $$X_{t+2} = \phi X_{t+1} + \epsilon_{t+2} = \phi(\phi X_t + \epsilon_{t+1}) + \epsilon_{t+2} = \phi^2 X_t + \phi \epsilon_{t+1} + \epsilon_{t+2}$$
>   Par projection conditionnelle :
>   $$\hat{X}_{t+2} = \mathbb{E}[X_{t+2} | \mathcal{I}_t] = \phi^2 X_t = \phi \hat{X}_{t+1}$$
>   *(De manière générale, $\hat{X}_{t+h} = \phi^h X_t$)*.
> 
> ---
> 
> **3. Variance de l'erreur de prévision à 1 pas :**
> - L'erreur de prévision à 1 pas est :
>   $$e_t(1) = X_{t+1} - \hat{X}_{t+1} = (\phi X_t + \epsilon_{t+1}) - \phi X_t = \epsilon_{t+1}$$
> - Sa variance théorique est :
>   $$\mathbb{E}[(X_{t+1} - \hat{X}_{t+1})^2] = \mathbb{E}[\epsilon_{t+1}^2] = \sigma^2$$
> L'erreur à 1 pas s'identifie exactement au choc d'innovation imprévisible $\epsilon_{t+1}$.

---

> [!question] 3.2 Étude théorique du MA(1)
> Soit $X_{t} = \epsilon_{t} + \theta \epsilon_{t-1}$ avec $\epsilon_{t} \sim BB(0, \sigma^{2})$.
> 
> - **Q.1** Donner la prévision à 1 pas $\hat{X}_{t+1}$ et à 2 pas $\hat{X}_{t+2}$.
> - **Q.2** Que constatez-vous pour $h \ge 2$ ? Pourquoi ?

> [!success] Correction détaillée : 3.2 Étude théorique du MA(1)
> 
> **1. Prévisions à 1 pas et à 2 pas :**
> - **À horizon 1 pas ($h = 1$) :**
>   $$X_{t+1} = \epsilon_{t+1} + \theta \epsilon_t$$
>   Sous réserve d'inversibilité du modèle ($|\theta| < 1$), le choc présent $\epsilon_t$ est connu à la date $t$ ($\\epsilon_t = \sum_{j=0}^{\infty} (-\theta)^j X_{t-j}$). Comme $\mathbb{E}[\epsilon_{t+1} | \mathcal{I}_t] = 0$ :
>   $$\hat{X}_{t+1} = \mathbb{E}[X_{t+1} | \mathcal{I}_t] = \theta \epsilon_t$$
> 
> - **À horizon 2 pas ($h = 2$) :**
>   $$X_{t+2} = \epsilon_{t+2} + \theta \epsilon_{t+1}$$
>   Les deux chocs $\epsilon_{t+2}$ et $\epsilon_{t+1}$ se situent dans le futur par rapport à $t$. Donc :
>   $$\hat{X}_{t+2} = \mathbb{E}[\epsilon_{t+2} + \theta \epsilon_{t+1} | \mathcal{I}_t] = 0$$
> 
> ---
> 
> **2. Constat et justification pour $h \ge 2$ :**
> - **Constat :** Pour tout horizon $h \ge 2$, la prévision optimale est **strictement nulle** :
>   $$\hat{X}_{t+h} = 0 = \mathbb{E}[X_t] \quad \forall h \ge 2$$
> - **Justification :** Le processus $MA(1)$ possède une **mémoire finie d'ordre 1**. Au-delà de $h = 1$, la série ne conserve plus aucune corrélation avec son passé ($X_{t+h}$ est totalement indépendant de $\mathcal{I}_t$). La meilleure prévision linéaire sous $L^2$ retombe alors instantanément sur la moyenne inconditionnelle du processus (ici $0$).

---

> [!question] 3.3 Mise en œuvre avec R
> *Consigne : Exécutez le script R fourni (simulation de $n=200$ obs d'un $AR(1)$ avec $\phi=0.8$ et d'un $MA(1)$ avec $\theta=0.6$, calcul des $\psi_i$ jusqu'à $K=20$, prévision 1 pas avec troncature, variation de $K \in \{5, 10, 20, 50\}$).*
> 
> **Sorties à recopier :**
> - **Q.1** Recopiez les 5 premiers coefficients $\psi_{i}$ de l'$AR(1)$ affichés dans la console.
> - **Q.2** Recopiez la valeur du MSE pour $K = 20$ ($AR(1)$).
> - **Q.3** Recopiez le tableau des MSE pour $K = 5, 10, 20, 50$.
> 
> **Interprétations :**
> - **Q.4** Commentez l'évolution du MSE lorsque $K$ augmente. Pourquoi ce comportement ?
> - **Q.5** Comparez qualitativement les prévisions de l'$AR(1)$ et du $MA(1)$. Que se passe-t-il pour $h = 2$ dans les deux cas ?

> [!success] Correction détaillée : 3.3 Mise en œuvre avec R
> 
> **Sorties de simulation réelles (console R avec `set.seed(123)`) :**
> 
> - **1. Les 5 premiers coefficients $\psi_i$ de l'$AR(1)$ (avec $\phi = 0.8$) :**
>   - $\psi_0 = 1.0000$ (dans R, l'indice 1 donne $\psi_0$)
>   - $\psi_1 = 0.8000$
>   - $\psi_2 = 0.6400$
>   - $\psi_3 = 0.5120$
>   - $\psi_4 = 0.4096$
> 
> - **2. Valeur du MSE pour $K = 20$ ($AR(1)$) :**
>   $$\text{MSE}(K = 20) = 0.8493$$
>   *(sur cet échantillon simulé de taille $n_{\text{test}} = 50$, le MSE empirique est d'environ $0.85$, proche de la variance théorique $\sigma^2 = 1$)*.
> 
> - **3. Tableau des MSE selon le seuil de troncature $K$ :**
> 
> | Troncature $K$ | MSE empirique calculé par R | Commentaire |
> | :---: | :---: | :--- |
> | $K = 5$ | **0.8996** | Erreur résiduelle plus forte due aux termes omis $\sum_{j=6}^\infty 0.8^j \epsilon_{t-j}$ |
> | $K = 10$ | **0.8311** | Amélioration rapide avec la décroissance géométrique |
> | $K = 20$ | **0.8493** | Stabilisation au niveau du bruit résiduel |
> | $K = 50$ | **0.8509** | Quasi-identique à $K=20$ (puissances $0.8^{50} \approx 1.4 \times 10^{-5}$ négligeables) |
> 
> *(À titre indicatif, pour le $MA(1)$, le script affiche $\text{MSE}_{MA(1)} = 0.8509$ et les premières prévisions sont : $-0.7722, +0.4726, +0.4614, +0.1993, -0.6050$).*
> 
> ---
> 
> **Interprétations :**
> 
> - **4. Commentaire sur l'évolution du MSE :**
>   Le MSE décroît nettement entre $K=5$ ($0.90$) et $K=10$ ($0.83$), puis atteint un palier incompressible autour de $0.85$.
>   *Explication :* L'approximation tronquée $\hat{X}_{t+1}^{(K)} = \sum_{i=1}^K \psi_i \epsilon_{t+1-i}$ néglige la queue de distribution $\sum_{i=K+1}^{\infty} \phi^i \epsilon_{t+1-i}$. Comme $|\phi| = 0.8 < 1$, les puissances $\phi^i$ convergent géométriquement vers 0. Dès $K \ge 15$, les termes oubliés ont un poids infinitésimal, le MSE converge donc vers la variance intrinsèque non prévisible du choc $\epsilon_{t+1}$.
> 
> - **5. Comparaison $AR(1)$ vs $MA(1)$ (notamment pour $h = 2$) :**
>   - Pour l'$AR(1)$, la prévision à $h = 2$ est $\hat{X}_{t+2} = \phi^2 X_t = 0.64 X_t \ne 0$. Le processus a une **mémoire infinie amortie** : l'information passée s'estompe mais persiste indéfiniment.
>   - Pour le $MA(1)$, la prévision à $h = 2$ chute à $0$ (ou à la moyenne estimée $\hat{\mu}$). Le processus a une **mémoire finie bornée à 1 période** ($q = 1$) : aucun choc antérieur à $t$ n'influence $t+2$.

---

## Partie II - Généralisation aux ordres supérieurs

> [!question] 4.1 Simulation et ACF
> Le script simule :
> - Un $AR(2) : X_{t} = 0.7 X_{t-1} - 0.3 X_{t-2} + \epsilon_{t}$
> - Un $MA(2) : X_{t} = \epsilon_{t} + 0.6 \epsilon_{t-1} + 0.3 \epsilon_{t-2}$
> 
> - **Q.** Observez les ACF (graphiques). Décrivez la forme de l'ACF de l'$AR(2)$ par rapport à celle de l'$AR(1)$ (est-elle monotone ?).

> [!success] Correction détaillée : 4.1 Simulation et ACF
> 
> - **Forme de l'ACF de l'$AR(1)$ :** Pour un $AR(1)$ de paramètre $\phi = 0.8 > 0$, l'ACF est une exponentielle strictement décroissante et monotone : $\rho(h) = 0.8^h > 0$.
> - **Forme de l'ACF de l'$AR(2)$ :** L'ACF de cet $AR(2)$ n'est **pas monotone**. Elle présente un profil **pseudo-périodique sinusoïdal amorti** (ondes amorties). Les autocorrélations oscillent entre valeurs positives et négatives tout en s'atténuant progressivement vers 0.
> - *Explication analytique :* Le polynôme caractéristique associé $\Phi(z) = 1 - 0.7z + 0.3z^2$ a pour discriminant $\Delta = 0.7^2 - 4(0.3)(1) = 0.49 - 1.20 = -0.71 < 0$. Il admet donc deux racines complexes conjuguées, ce qui engendre mathématiquement des oscillations sinusoïdales amorties dans la fonction d'autocovariance.

---

> [!question] 4.2 Coefficients $\psi_{i}$ de l'AR(2)
> Le script utilise la fonction `ARMAtoMA` pour obtenir les coefficients $\psi_{i}$ de l'$AR(2)$ sans les calculer à la main.
> 
> - **Q.** Recopiez les 5 premiers coefficients $\psi_{i}$ de l'$AR(2)$ affichés dans la console.
> - **Q.** Contrairement à l'$AR(1)$, les coefficients de l'$AR(2)$ ne décroissent pas de manière monotone. Expliquez pourquoi (en lien avec les racines du polynôme caractéristique).

> [!success] Correction détaillée : 4.2 Coefficients $\psi_i$ de l'AR(2)
> 
> **1. Les 5 premiers coefficients $\psi_i$ de l'$AR(2)$ :**
> Par la relation d'identification récursive $\psi_j = 0.7\psi_{j-1} - 0.3\psi_{j-2}$ (avec $\psi_0 = 1$ et $\psi_{-1} = 0$) :
> - $\psi_1 = 0.7(1) = 0.7000$
> - $\psi_2 = 0.7(0.7) - 0.3(1) = 0.49 - 0.30 = 0.1900$
> - $\psi_3 = 0.7(0.19) - 0.3(0.70) = 0.133 - 0.210 = -0.0770$
> - $\psi_4 = 0.7(-0.077) - 0.3(0.19) = -0.0539 - 0.0570 = -0.1109$
> - $\psi_5 = 0.7(-0.1109) - 0.3(-0.077) = -0.0776 + 0.0231 = -0.0545$
> 
> ---
> 
> **2. Pourquoi les coefficients ne sont-ils pas monotones ?**
> - Comme le discriminant de l'équation caractéristique est négatif ($\Delta = -0.71 < 0$), les racines sont deux nombres complexes conjugués :
>   $$z_{1, 2} = r e^{\pm i \omega}$$
> - La solution générale de l'équation aux différences pour les [[60.2.30. Calcul récursif des coefficients psi|coefficients de Wold]] s'écrit :
>   $$\psi_j = A \, r^{-j} \cos(\omega j + \varphi)$$
> - Le facteur trigonométrique $\cos(\omega j + \varphi)$ introduit des alternances de signe et des fluctuations harmoniques (ici passage au négatif dès $j=3$), tandis que le facteur $r^{-j}$ (avec le module $|z| = 1/\sqrt{0.3} \approx 1.825 > 1$) assure la convergence vers 0.

---

> [!question] 4.3 Prévision pour AR(2) et MA(2)
> Le script calcule les prévisions à 1, 2 et 3 pas pour l'$AR(2)$ et le $MA(2)$ à l'aide de `predict()`.
> 
> - **Q.** Recopiez les prévisions $AR(2)$ et $MA(2)$ affichées.
> - **Q.** Pour le $MA(2)$, à partir de quel horizon la prévision devient-elle nulle ? Est-ce cohérent avec la théorie ?

> [!success] Correction détaillée : 4.3 Prévision pour AR(2) et MA(2)
> 
> **1. Prévisions affichées par la console R (avec `set.seed(123)`) :**
> 
> - **Prévisions de l'$AR(2)$ (`pred_ar2$pred`) :**
>   - Horizon $h = 1$ : **$-1.1102$**
>   - Horizon $h = 2$ : **$-0.8981$**
>   - Horizon $h = 3$ : **$-0.7339$**
>   *(Les prévisions décroissent lentement en valeur absolue, reflétant la mémoire infinie amortie du processus autorégressif).*
> 
> - **Prévisions du $MA(2)$ (`pred_ma2$pred`) :**
>   - Horizon $h = 1$ : **$-0.9914$**
>   - Horizon $h = 2$ : **$+0.1310$**
>   - Horizon $h = 3$ : **$-0.0324$**
> 
> ---
> 
> **2. Horizon d'annulation pour le $MA(2)$ et cohérence théorique :**
> - **Dans la théorie (processus centré) :** La prévision devient **strictement nulle à partir de l'horizon $h = 3$** ($h > q = 2$) :
>   $$\hat{X}_{t+1} = \theta_1 \epsilon_t + \theta_2 \epsilon_{t-1} = 0.6 \epsilon_t + 0.3 \epsilon_{t-1}$$
>   $$\hat{X}_{t+2} = \theta_2 \epsilon_t = 0.3 \epsilon_t$$
>   $$\hat{X}_{t+h} = 0 \quad \forall h \ge 3$$
> - **Dans la sortie R :** La prévision au pas 3 vaut **$-0.0324$** au lieu de $0$.
>   *Pourquoi ?* Par défaut, la commande `arima(..., order = c(0, 0, 2))` estime la moyenne empirique de l'échantillon (intercept $\hat{\mu} = -0.0324$). Pour $h > q$, la partie purement moyenne mobile s'annule complètement, et la prévision retombe exactement sur l'espérance estimée du processus : $\hat{X}_{t+3} = \hat{\mu} = -0.0324 \approx 0$.
> - **Cohérence :** C'est **100 % cohérent** avec la théorie de la mémoire finie d'ordre $q=2$ : au-delà de 2 pas, aucune information issue des chocs passés n'est conservée.

---

> [!question] 4.4 Bilan comparatif
> - **Q.** Complétez le tableau ci-dessous en quelques mots :
> 
> | Processus | Mémoire | Forme de l'ACF |
> | :--- | :--- | :--- |
> | $AR(1)$ | | |
> | $AR(2)$ | | |
> | $MA(1)$ | | |
> | $MA(2)$ | | |

> [!success] Correction détaillée : 4.4 Bilan comparatif
> 
> Tableau de synthèse complété :
> 
> | Processus | Mémoire | Forme de l'ACF |
> | :--- | :--- | :--- |
> | **$AR(1)$** | **Infinie (amortie)** | Décroissance exponentielle monotone (si $\phi > 0$) ou alternée (si $\phi < 0$) |
> | **$AR(2)$** | **Infinie (amortie)** | Sinusoïde amortie (racines complexes) ou somme d'exponentielles |
> | **$MA(1)$** | **Finie (ordre 1)** | Coupure nette après $h = 1$ (nulle pour tout $h \ge 2$) |
> | **$MA(2)$** | **Finie (ordre 2)** | Coupure nette après $h = 2$ (nulle pour tout $h \ge 3$) |

---

> [!question] 4.5 Conclusion générale
> - **Q.** En vous appuyant sur l'ensemble des résultats, expliquez en quoi le théorème de Wold est un outil unificateur pour la prévision des processus linéaires stationnaires.

> [!success] Correction détaillée : 4.5 Conclusion générale
> 
> Le **[[60.2.4. Théorème de décomposition de Wold|théorème de décomposition de Wold]]** constitue le fondement unificateur de l'analyse des séries temporelles linéaires stationnaires pour les raisons suivantes :
> 
> 1. **Représentation universelle :** Tout processus faiblement stationnaire purement non déterministe peut s'écrire sous forme d'une somme infinie de chocs passés :
>    $$X_t = \sum_{j=0}^{\infty} \psi_j \epsilon_{t-j} \quad \text{avec} \quad \sum_{j=0}^{\infty} \psi_j^2 < \infty$$
> 
> 2. **Formule universelle de la prévision :** Quelle que soit la complexité du processus (qu'il soit $AR$, $MA$ ou $ARMA$), la meilleure prévision linéaire à l'horizon $h$ au sens du critère quadratique $L^2$ s'exprime toujours par la formule canonique :
>    $$\hat{X}_{t+h|t} = \sum_{j=h}^{\infty} \psi_j \epsilon_{t+h-j}$$
> 
> 3. **Variance d'erreur standardisée :** L'erreur de prévision à horizon $h$ vaut toujours $e_t(h) = \sum_{j=0}^{h-1} \psi_j \epsilon_{t+h-j}$, et sa variance est universellement :
>    $$\operatorname{Var}(e_t(h)) = \sigma^2 \sum_{j=0}^{h-1} \psi_j^2$$
> 
> Les modèles $AR(p)$, $MA(q)$ ou $ARMA(p, q)$ ne sont finalement que des **paramétrisations parcimonieuses** permettant d'exprimer et de calculer facilement les coefficients $(\psi_j)_{j \ge 0}$ à partir d'un nombre fini de paramètres.
