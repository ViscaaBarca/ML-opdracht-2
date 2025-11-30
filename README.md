Projectbeschrijving
In dit project voorspellen we het aantal verhuurde items (fietsen) per uur op basis van historische data en weersomstandigheden. Het doel is om een robuust machine learning model te ontwikkelen dat rekening houdt met complexe tijdreelsemementen zoals trends, seizoensinvloeden en vakantiedagen.
Dit project maakt gebruik van geavanceerde Time Series Feature Engineering en vergelijkt statistische modellen (SARIMAX) met moderne Machine Learning technieken (XGBoost, Hybride modellen).

Methodologie & Aanpak
Het project is opgebouwd in een gestructureerd Jupyter Notebook, verdeeld over vier fases:
1. Exploratieve Data Analyse (EDA)
Een diepgaande analyse van de tijdreeksstructuur:
Stationariteitstests: Uitgevoerd met de Augmented Dickey-Fuller (ADF) test.
Decompositie: Vergelijking tussen additieve en multiplicatieve decompositie van trend, seizoen en residu.
Correlatie: Analyse van weersinvloeden en multicollineariteit.
Autocorrelatie: Analyse van ACF en PACF plots om significante lags te bepalen.
2. Time Series Feature Engineering
Het vertalen van tijdspatronen naar numerieke features:
Fourier Analyse: Gebruik van een Periodogram om dominante frequenties te vinden en deze om te zetten in Fourier-termen (sinus/cosinus) voor jaarlijkse en wekelijkse cycli.
Lag Features: Creatie van vertraagde variabelen (lags) en rolling means op basis van PACF-inzichten.
Deterministische Processen: Modelleren van lineaire trends.
3. Modelleren
Een breed scala aan modellen is getraind, getuned (via TimeSeriesSplit cross-validatie) en geëvalueerd:
Baselines: Lineaire Regressie (Ridge).
Ensemble Modellen: Random Forest & XGBoost.
Tijdreeksmodellen: Iteratieve verbetering van SARIMA naar SARIMAX met exogene variabelen.
Hybride Modellen: Een combinatie van Lineaire Regressie (voor trend-extrapolatie) en XGBoost (voor residuele patronen).
4. Evaluatie & Conclusie
Modellen zijn beoordeeld op RMSE (Root Mean Squared Error). Er is een specifiek advies geformuleerd op basis van zowel modelprestaties als robuustheid (extrapolatie-vermogen).

Resultaten
Model	Validatie RMSE	Opmerking
XGBoost	~49.87	Beste score op validatieset, vangt complexe interacties goed.
Random Forest	~59.58	Robuust en stabiel.
Hybride (Lin+XGB)	~76.80	Aanbevolen model vanwege vermogen om toekomstige trends te extrapoleren.
Ridge Regression	~91.46	Sterke baseline.
SARIMAX	~136.63	Minder accuraat dan ML-modellen door complexiteit van interacties.
Aanbeveling
Hoewel tree-based modellen (XGBoost) de laagste foutmarge hadden op de validatieset, adviseren wij het Hybride Model. Tree-based modellen kunnen niet extrapoleren (voorspellen buiten de gekende range), wat problematisch is bij een groeiende trend. Het Hybride model scheidt de trend (lineair) van de seizoensinvloeden (XGBoost) en is daardoor toekomstbestendiger.
