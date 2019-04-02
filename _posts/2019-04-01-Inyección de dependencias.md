# Inyección de dependencias
## ¿Qué es?

Es un patrón de diseño orientado a objetos, en el que se suministran objetos a una clase en lugar de ser la propia clase la que cree dichos objetos. Esos objetos cumplen contratos que necesitan nuestras clases para poder funcionar (de ahí el concepto de dependencia). Nuestras clases no crean los objetos que necesitan, sino que se los suministra otra clase 'contenedora' que inyectará la implementación deseada a nuestro contrato.

## Ventajas

  - La inyección de dependencia le permite al cliente la flexibilidad de ser configurable. Sólo el comportamiento del cliente es fijo. El cliente puede actuar sobre cualquier cosa que admita la interfaz intrínseca que el cliente espera.
  
  - La inyección de dependencia se puede utilizar para externalizar los detalles de configuración de un sistema en archivos de configuración, lo que permite que el sistema se reconfigure sin recompilación. Se pueden escribir configuraciones separadas para diferentes situaciones que requieren diferentes implementaciones de componentes. Esto incluye, pero no se limita a, pruebas.
  
  - Como la inyección de dependencia no requiere ningún cambio en el comportamiento del código, se puede aplicar al código heredado como una refactorización . El resultado es clientes que son más independientes y que son más fáciles de realizar una prueba de unidad en forma aislada utilizando talones u objetos simulados que simulan otros objetos que no están bajo prueba. Esta facilidad de prueba es a menudo el primer beneficio observado cuando se usa la inyección de dependencia.
  
  - La inyección de dependencia le permite al cliente eliminar todo el conocimiento de una implementación concreta que necesita usar. Esto ayuda a aislar al cliente del impacto de los cambios y defectos de diseño. Promueve la reutilización, la testabilidad y la mantenibilidad.
  
  - Reducción del código de repetición en los objetos de la aplicación, ya que todo el trabajo para inicializar o configurar las dependencias es manejado por un componente del proveedor.
  
  - La inyección de dependencia permite el desarrollo concurrente o independiente. Dos desarrolladores pueden desarrollar de forma independiente clases que se usan entre sí, mientras que solo necesitan conocer la interfaz a través de la cual se comunicarán las clases. Los complementos a menudo son desarrollados por tiendas de terceros que nunca hablan con los desarrolladores que crearon el producto que usa los complementos.
  
  - La inyección de dependencia disminuye el acoplamiento entre una clase y su dependencia

## Desventajas
