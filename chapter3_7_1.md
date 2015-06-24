#### Just In Time (JIT) Compilation


O **bytecode** Java interpretado não são tão rápido quanto os códigos nativos, para cobrir esse problema de performance, a JVM verifica métodos críticos (regiões que executam constantemente, por exemplo) e compila para o código nativo. Esse código nativo será armazenado dentro do **cache de código** em uma região fora da heap. A JVM tenta escolher as regiões mais críticas para que mesmo com o gasto memória e poder computacional de compilar o código para nativo, seja uma decisão vantajosa.