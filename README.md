# Zeppelin Chart

[Zeppelin](https://zeppelin.apache.org/) is a web based notebook for interactive data analytics with Spark, SQL and Scala.
This chart is a clone of stable/zeppelin that configures zeppelin to connect to external Yarn/Spark cluster. 

## Chart Details

## Installing the Chart

To install the chart:

```
$ helm install . --set hadoop.configMapName=<configMap name> --set hadoop.configMapName=<configMap name> --set driver.host=<node address>
```

## Configuration

The following table lists the configurable parameters of the Zeppelin chart and their default values.

| Parameter                            | Description                                                       | Default                                                    |
| ------------------------------------ | ----------------------------------------------------------------- | ---------------------------------------------------------- |
| `zeppelin.image`                     | Zeppelin image                                                    | `dylanmei/zeppelin:{VERSION}`                              |
| `zeppelin.resources`                 | Resource limits and requests                                      | `limits.memory=4096Mi, limits.cpu=2000m`                   |
| `hadoop.useConfigMap`                | Use external Hadoop configuration for Spark executors             | `false`                                                    |
| `hadoop.configMapName`               | Name of the hadoop config map to use (must be in same namespace)  | `hadoop-config`                                            |
| `hadoop.configPath`                  | Path in the Zeppelin image where the Hadoop config is mounted     | `/usr/hadoop-2.7.3/etc/hadoop`                             |
| `spark.useImage`                     | Mount spark from the container instead of downloading             | `true`                                                     |
| `spark.download.link`                | Spark download link if useCOntainer==false                        | ``                                                         |
| `spark.image.tag`                    | Image tag with Spark under image.path                             | `spark:v2.3.3`                                             |
| `spark.image.path`                   | Path to spark in image                                            | `/opt/spark`                                               |
| `spark.additionalJars.enabled`       | Enable mounting of additional jars from pvc                       | `false`                                                    |
| `spark.additionalJars.claimName`     | PVC resource name from the same namespace                         | `dummy-pvc`                                                |
| `spark.sparkDefaults.enabled`        | Enable mounting spark-defaults from the configmap                 | `false`                                                    |
| `spark.sparkDefaults.configMapName`  | --                                                                | `spark-defaults`                                           |
| `spark.driver.host`                  | Host from which spark driver will be acessible(through NodePort)  | `localhost`                                                |
| `spark.driver.port`                  | Port from which spark driver will be acessible(through NodePort)  | `30321`                                                    |
| `spark.env`                          | Additional environment variables to define                        | `see values`                                               |
| `spark.submit_options`               | additional submit options for spark                               | `e.g. `                                                    |
| `ingress.enabled`                    | Enable ingress                                                    | `false`                                                    |
| `ingress.annotations`                | Ingress annotations                                               | `{}`                                                       |
| `ingress.hosts`                      | Ingress Hostnames                                                 | `["zeppelin.local"]`                                       |
| `ingress.path`                       | Path within the URL structure                                     | `/`                                                        |
| `ingress.tls`                        | Ingress TLS configuration                                         | `[]`                                                       |
| `nodeSelecor`                        | Node selector for the Zeppelin deployment                         | `{}`                                                       |

