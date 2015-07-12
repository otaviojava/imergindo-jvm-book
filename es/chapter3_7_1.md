#### Just In Time (JIT) Compilation


Los **bytecode** Java interpretados no son tan rapidos como los códigos nativos, para cubrir este problema de performance, la JVM verifica métodos críticos (regiones que se ejecutan constantemente, por ejemplo) y compila para el código nativo. Este código nativo será almacenado dentro de **cache de código** en uma región fuera del heap. La JVM intenta escoger las regiones mas críticas para que incluso con el gasto de memoria y poder computacional de compilar el código para nativo, sea una decisión ventajosa.