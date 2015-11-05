#### Just In Time (JIT) Compilation


Los **bytecode** Java interpretados no son tan rápidos como el código nativo, para cubrir este problema de performance, la JVM verifica métodos críticos (regiones que se ejecutan repetidamente, por ejemplo) y compila para él código nativo. Este código nativo será almacenado dentro de **cache de código** en una región fuera del *heap*. La JVM intenta escoger las regiones más críticas para que incluso con el gasto de memoria y poder computacional de compilar el código para nativo, sea una decisión ventajosa.
