---
title: Envío de un trabajo de .NET para Apache Spark a Azure HDInsight
description: Aprenda a enviar un trabajo de .NET para Apache Spark a Azure HDInsight mediante spark-submit y Apache Livy.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 74be4ecf33a9a881633da0630fa1c1a4bf0b19c6
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688168"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a>Envío de un trabajo de .NET para Apache Spark a Azure HDInsight

Hay dos maneras de implementar el trabajo de .NET para Apache Spark en HDInsight: `spark-submit` y Apache Livy.

## <a name="deploy-using-spark-submit"></a>Implementación mediante spark-submit

Puede usar el comando [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) para enviar trabajos de .NET para Apache Spark a Azure HDInsight.

1. Vaya al clúster de HDInsight de Spark en Azure Portal y luego seleccione **SSH e inicio de sesión del clúster**.

2. Copie la información de inicio de sesión de SSH y pegue el inicio de sesión en un terminal. Inicie sesión en el clúster con la contraseña que se ha establecido durante la creación del clúster. Debería ver mensajes de bienvenida a Ubuntu y Spark.

3. Use el comando **spark-submit** para ejecutar la aplicación en el clúster de HDInsight. Recuerde reemplazar **mycontainer** y **mystorageaccount** en el script de ejemplo con los nombres reales del contenedor de blobs y la cuenta de almacenamiento. Recuerde también reemplazar el archivo microsoft-spark jar por la versión de Spark y .NET para Apache Spark que se use.

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a>Implementación mediante Apache Livy

Puede usar [Apache Livy](https://livy.incubator.apache.org/), la API de REST de Apache Spark, para enviar .NET para trabajos de Apache Spark a un clúster Azure HDInsight Spark. Para más información, vea [Trabajos remotos con Apache Livy](/azure/hdinsight/spark/apache-spark-livy-rest-interface).

Puede ejecutar el siguiente comando en Linux usando `curl`:

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.dotnet.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a>Pasos siguientes

* [Introducción a .NET para Apache Spark](../tutorials/get-started.md)
* [Implementación de una aplicación de .NET para Apache Spark en Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Documentación de HDInsight](/azure/hdinsight/)
