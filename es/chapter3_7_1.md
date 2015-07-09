#### Just In Time (JIT) Compilation


El **bytecode** Java interpretado no es tan rápido como el código nativo, y para cubrir ese problema de performance, la JVM verifica los métodos críticos (regiones que se ejecutan constantemente, por ejemplo) y compila ellos a código nativo. Ese código nativo será almacenado en el **cache de código** una región fuera del heap. La JVM escoge las regiones más críticas para que el gasto de memoria y poder computacional de compilar a código nativo, sea una decisión ventajosa.