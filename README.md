# Principios SOLID

Los principios **SOLID** son cinco buenas prácticas de diseño orientado a objetos que ayudan a crear software más mantenible, extensible y flexible. Fueron popularizados por **Robert C. Martin (Uncle Bob)**.

---

## 🟡 S - Single Responsibility Principle (SRP)

> "Una clase debe tener una, y solo una, razón para cambiar."

Cada clase o módulo debe encargarse de una única funcionalidad del sistema. Separar responsabilidades evita que un cambio en una parte afecte innecesariamente a otras.

**Ejemplo:**

```java
// ❌ Mala práctica
class ReportManager {
    void generateReport() {...}
    void saveToPDF() {...}
    void sendByEmail() {...}
}

// ✅ Mejor práctica
class ReportGenerator {...}
class PDFExporter {...}
class EmailSender {...}

<<<<<<< HEAD










## 🌐 I - Principio de Segregación de Interfaces (ISP)

> "Los clientes no deben verse obligados a depender de interfaces que no utilizan"

### ❌ Ejemplo que viola el ISP
```java
interface DispositivoOficina {
    void imprimir();
    void escanear();
    void faxear();
}

class ImpresoraBasica implements DispositivoOficina {
    // Obligada a implementar métodos que no usa
    public void imprimir() { ... }
    public void escanear() { 
        throw new UnsupportedOperationException(); 
    }
    public void faxear() { 
        throw new UnsupportedOperationException(); 
    }
}


=======
# Principio O – Open/Closed (Abierto/Cerrado)

## Definición
El software debe estar **abierto a la extensión pero cerrado a la modificación**. Esto significa que se debe poder agregar nuevas funcionalidades sin modificar las clases existentes.

---

## ❌ Ejemplo Incorrecto (Mala práctica)

```java
class PDFGenerator {
    public void generatePDF(String type, String content) {
        if (type.equals("report")) {
            System.out.println("Generating report PDF: " + content);
        } else if (type.equals("invoice")) {
            System.out.println("Generating invoice PDF: " + content);
        }
        // Si queremos agregar un nuevo tipo de PDF, debemos modificar esta clase.
    }
}

public class Main {
    public static void main(String[] args) {
        PDFGenerator pdfGenerator = new PDFGenerator();
        pdfGenerator.generatePDF("report", "Annual Report Content.");
        pdfGenerator.generatePDF("invoice", "Invoice #1234 Content.");
    }
}
interface PDFGenerator {
    void generatePDF(String content);
}

class ReportPDFGenerator implements PDFGenerator {
    @Override
    public void generatePDF(String content) {
        System.out.println("Generating report PDF: " + content);
    }
}

class InvoicePDFGenerator implements PDFGenerator {
    @Override
    public void generatePDF(String content) {
        System.out.println("Generating invoice PDF: " + content);
    }
}

public class Main {
    public static void main(String[] args) {
        PDFGenerator reportPDF = new ReportPDFGenerator();
        PDFGenerator invoicePDF = new InvoicePDFGenerator();

        reportPDF.generatePDF("Annual Report Content.");
        invoicePDF.generatePDF("Invoice #1234 Content.");
    }
}
L – Liskov Substitution Principle
👉 Principio de Sustitución de Liskov

Las subclases deben poder sustituir a sus clases padre sin afectar el funcionamiento.

✔ Qué significa:
Si una clase hija no se comporta como su clase padre, habrá errores al usarla.

🧠 Ejemplo:

class Bird {
    public void fly() {
        System.out.println("Puedo volar");
    }
}

class Penguin extends Bird {
    // ❌ Un pingüino no puede volar, pero estamos forzando una función que no aplica.
}

    Aquí se rompe el principio. Lo correcto sería tener una jerarquía diferente donde Bird no asuma que todas las aves vuelan.



## 🌐 I - Principio de Segregación de Interfaces (ISP)

> "Los clientes no deben verse obligados a depender de interfaces que no utilizan"

### ❌ Ejemplo que viola el ISP
```java
interface DispositivoOficina {
    void imprimir();
    void escanear();
    void faxear();
}

class ImpresoraBasica implements DispositivoOficina {
    // Obligada a implementar métodos que no usa
    public void imprimir() { ... }
    public void escanear() { 
        throw new UnsupportedOperationException(); 
    }
    public void faxear() { 
        throw new UnsupportedOperationException(); 
    }
}
### D:  El Dependency Inversion Principle dice:

“Los módulos de alto nivel no deben depender de módulos de bajo nivel. Ambos deben depender de abstracciones.
Las abstracciones no deben depender de los detalles, los detalles deben depender de las abstracciones.”

Ejemplo 1: Notificaciones
java
Copiar
Editar
interface Notification {
    void send(String message);
}

class EmailNotification implements Notification {
    public void send(String message) {
        System.out.println("Email: " + message);
    }
}

class NotificationManager {
    private Notification notification;

    public NotificationManager(Notification notification) {
        this.notification = notification;
    }

    public void notifyUser(String message) {
        notification.send(message);
    }
}

public class Main {
    public static void main(String[] args) {
        Notification email = new EmailNotification();
        NotificationManager manager = new NotificationManager(email);
        manager.notifyUser("Hola!");
    }
}
Explicación: NotificationManager depende de la interfaz Notification (abstracción), no de una clase concreta. Esto permite cambiar el tipo de notificación sin modificar NotificationManager.




>>>>>>> 37418240f27306d62aa23e6ea150d62948a98958

