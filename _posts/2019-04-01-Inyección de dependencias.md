# Inyección de dependencias
## ¿Qué es?

Es un patrón de diseño orientado a objetos, en el que se suministran objetos a una clase en lugar de ser la propia clase la que cree dichos objetos. Esos objetos cumplen contratos que necesitan nuestras clases para poder funcionar (de ahí el concepto de dependencia). Nuestras clases no crean los objetos que necesitan, sino que se los suministra otra clase 'contenedora' que inyectará la implementación deseada a nuestro contrato.

La inyección de dependencia involucra cuatro roles:

  - El servicio objeto (s) que se utilizará.
  - El objeto cliente que depende de los servicios que usa.
  - Las interfaces que definen cómo el cliente puede utilizar los servicios.
  - El inyector , que es responsable de construir los servicios e inyectarlos en el cliente.
  
Cualquier objeto que pueda ser usado puede ser considerado un servicio. Cualquier objeto que use otros objetos puede ser considerado un cliente. Los nombres no tienen nada que ver con lo que son los objetos y todo lo que tiene que ver con el papel que desempeñan los objetos en cualquier inyección.

Las interfaces son los tipos que el cliente espera que sean sus dependencias. Un problema es lo que hacen accesible. Pueden ser realmente tipos de interfaz implementados por los servicios, pero también pueden ser clases abstractas o incluso servicios concretos, aunque esto último violaría el DIP y sacrificaría el desacoplamiento dinámico que permite la prueba. Solo se requiere que el cliente no sepa cuáles son y, por lo tanto, nunca los trate como concretos, por ejemplo, al construirlos o extenderlos.

El cliente no debe tener un conocimiento concreto de la implementación específica de sus dependencias. Solo debe saber el nombre de la interfaz y la API . Como resultado, el cliente no tendrá que cambiar incluso si cambia lo que está detrás de la interfaz. Sin embargo, si la interfaz se modifica para que no sea una clase a un tipo de interfaz (o viceversa), el cliente deberá volver a compilarse. Esto es significativo si el cliente y los servicios se publican por separado. Este acoplamiento desafortunado es uno que la inyección de dependencia no puede resolver.

El inyector introduce los servicios en el cliente. A menudo, también construye el cliente. Un inyector puede conectar un gráfico de objeto muy complejo tratando un objeto como un cliente y más tarde como un servicio para otro cliente. El inyector puede ser en realidad muchos objetos trabajando juntos pero puede que no sea el cliente. El inyector puede ser referido por otros nombres tales como: ensamblador, proveedor, contenedor, fábrica, fabricante, resorte, código de construcción o principal.

### Tipos de inyección

  - Inyección de constructor: las dependencias se proporcionan a través del constructor de clase de un cliente.
    ~~~
    Client(Service service) {
        this.service = service;
    }
    ~~~
  - Inyección de setter: el cliente expone un método set que utiliza el inyector para inyectar la dependencia.
   ~~~
    public void setService(Service service) {
       this.service = service;
    }
    ~~~
  - Inyección de interfaz: la interfaz de la dependencia proporciona un método de inyección que inyectará la dependencia en cualquier cliente que se le pase. Los clientes deben implementar una interfaz que exponga un método de establecimiento que acepte la dependencia.
    ~~~
    // Service setter interface.
    public interface ServiceSetter {
        public void setService(Service service);
    }

    // Client class
    public class Client implements ServiceSetter {
        private Service service;

        // Set the service that this client is to use.
        @Override
        public void setService(Service service) {
            this.service = service;
        }
    }
    ~~~

## Ventajas

  - Permite al cliente la flexibilidad de ser configurable. Sólo el comportamiento del cliente es fijo. El cliente puede actuar sobre cualquier cosa que admita la interfaz intrínseca que el cliente espera.
  
  - Se puede utilizar para externalizar los detalles de configuración de un sistema en archivos de configuración, lo que permite que el sistema se reconfigure sin recompilación. Se pueden escribir configuraciones separadas para diferentes situaciones que requieren diferentes implementaciones de componentes. Esto incluye, pero no se limita a, pruebas.
  
  - Como la inyección de dependencia no requiere ningún cambio en el comportamiento del código, se puede aplicar al código heredado como una refactorización . El resultado es clientes que son más independientes y que son más fáciles de realizar una prueba de unidad en forma aislada utilizando talones u objetos simulados que simulan otros objetos que no están bajo prueba. Esta facilidad de prueba es a menudo el primer beneficio observado cuando se usa la inyección de dependencia.
  
  - Permite al cliente eliminar todo el conocimiento de una implementación concreta que necesita usar. Esto ayuda a aislar al cliente del impacto de los cambios y defectos de diseño. Promueve la reutilización, la testabilidad y la mantenibilidad.
  
  - Reducción del código de repetición en los objetos de la aplicación, ya que todo el trabajo para inicializar o configurar las dependencias es manejado por un componente del proveedor.
  
  - Permite el desarrollo concurrente o independiente. Dos desarrolladores pueden desarrollar de forma independiente clases que se usan entre sí, mientras que solo necesitan conocer la interfaz a través de la cual se comunicarán las clases. Los complementos a menudo son desarrollados por tiendas de terceros que nunca hablan con los desarrolladores que crearon el producto que usa los complementos.
  
  - Disminuye el acoplamiento entre una clase y su dependencia

## Desventajas

  - La inyección de dependencia crea clientes que exigen que los detalles de configuración sean suministrados por el código de construcción. Esto puede ser oneroso cuando hay valores predeterminados obvios disponibles.

  - La inyección de dependencia puede hacer que el código sea difícil de rastrear (leer) porque separa el comportamiento de la construcción. Esto significa que los desarrolladores deben consultar más archivos para seguir cómo funciona un sistema.
  
  - Los marcos de inyección de dependencia se implementan con reflexión o programación dinámica. Esto puede dificultar el uso de la automatización IDE, como "encontrar referencias", "mostrar jerarquía de llamadas" y refactorizaciones seguras.
  
  - La inyección de dependencia generalmente requiere un mayor esfuerzo de desarrollo por adelantado, ya que uno no puede convertirse en algo correcto cuando y donde se necesita, pero debe solicitar que se inyecte y luego asegurarse de que se haya inyectado.
La inyección de dependencia obliga a la complejidad a salir de las clases y a los vínculos entre clases que pueden no ser siempre deseables o fáciles de gestionar.

  - La inyección de dependencia puede fomentar la dependencia de un marco de inyección de dependencia.
