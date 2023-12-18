# Análisis de Clústeres en Conjunto de Datos de Diamantes
Este repositorio contiene dos scripts de Python que realizan análisis de clústeres en el conjunto de datos de diamantes. Los scripts utilizan las técnicas de K-Means y MeanShift para agrupar los diamantes en categorías similares.

## K-Means Clustering
El primer script, `kmeans_clustering.py`, utiliza la técnica de K-Means para agrupar los diamantes en cuatro categorías. A continuación, se presenta un resumen del código:

```python
    if __name__ == "__main__":
        # Leer el conjunto de datos de diamantes desde un archivo CSV
        dataset = pd.read_csv('./data/diamonds.csv')

        # Eliminar columnas no deseadas para el análisis de clústeres
        X = dataset.drop(['cut', 'color', 'clarity'], axis=1)

        # Aplicar K-Means con MiniBatchKMeans
        kmeans = MiniBatchKMeans(n_clusters=4, batch_size=8).fit(X)

        # Imprimir información sobre los resultados del clúster
        print("="*64)
        print("Total de centros: ", len(kmeans.cluster_centers_))
        print("="*64)
        print(kmeans.predict(X))
        print("="*64)

        # Agregar las etiquetas de los clústeres al conjunto de datos original
        dataset['group'] = kmeans.predict(X)
        print(dataset)
```    

## MeanShift Clustering
El segundo script, meanshift_clustering.py, utiliza la técnica de MeanShift para identificar automáticamente los clústeres presentes en el conjunto de datos. Aquí tienes un resumen del código:

```Python

        from sklearn.cluster import MeanShift

        if __name__ == "__main__":
            # Leer el conjunto de datos de diamantes desde un archivo CSV
            dataset = pd.read_csv('./data/diamonds.csv')

            # Eliminar columnas no deseadas para el análisis de clústeres
            X = dataset.drop(['cut', 'color', 'clarity'], axis=1)

            # Aplicar MeanShift para el análisis de clústeres
            meanshift = MeanShift().fit(X)

            # Imprimir información sobre los resultados del clúster
            print("="*64)
            print("Número máximo de etiquetas de clúster: ", max(meanshift.labels_))
            print("="*64)
            print(meanshift.cluster_centers_)

            # Agregar las etiquetas de los clústeres al conjunto de datos original
            dataset['meanshift'] = meanshift.labels_
            print("="*64)
            print(dataset)
```

Código generado por IA. Revisar y usar cuidadosamente. Más información sobre preguntas frecuentes.
Cada script realiza el análisis de clústeres y agrega las etiquetas de clústeres correspondientes al conjunto de datos original. Los resultados se imprimen para su revisión.

¡Diviértete explorando y analizando los clústeres en el conjunto de datos de diamantes!