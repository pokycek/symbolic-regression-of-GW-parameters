Zadání práce:

Symbolic regression of Gravitational waves parameters

Using the gravitational wave dataset available at Kaggle, train a model to detect gravitational waves. After training, apply symbolic regression to identify the parameters of the wave equation in the form:

$y_i(A_i,\omega_i;t)=A_i \cdot \sin{(\omega_i t)}$

where:

$A_i$ represents the amplitude,

$\omega_i$ is the frequency, and

$t$ is the time variable. 

This approach will enable both accurate detection and a deeper understanding of the underlying wave characteristics.

Pro učení modelu, na který dále bude uplatněna symbolická regrese byl použit dataset ze zadání:
Dataset má přibližně 70GB ve své komprimované formě, takže na Gitlabu se objeví pouze jeho malé demo, zbytek datasetu se dá stáhnout na soutěži na kaggle: https://www.kaggle.com/competitions/g2net-gravitational-wave-detection
Pro stáhnutí je potřeba mít ověřený účet na kaggle a souhlasit s pravidly soutěže.

Projekt obsahuje naučený model, ve složce models, tam také obsahuje ukázku, jak model načíst a použít, notebook neobsahuuje načtení dat, to je ve složce soruce, detection_model.ipynb, data se načtou tak, že se třídě class TimeSeriesDataset(Dataset) předá cesta na složku, kde jsou data, třída si složku projde rekurzivně a následně načte všechny .npy soubory, soubor musí obsahovat 3 časové řady, každá o 4096 hodnotách. Soubory samotné se poté načítají až když jsou potřeba, jinak by se nevešly do paměti.