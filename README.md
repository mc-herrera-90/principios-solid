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
