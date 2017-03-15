---
title: "Refactoring (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.preview"
  - "vs.csharp.refactoring.issues"
  - "vs.csharp.refactoring.buildwarning"
  - "VS.PreviewChanges"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#]"
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Als Umgestaltung wird die Optimierung von Code nach der Programmierung bezeichnet. Dabei wird die interne Struktur des Codes geändert, ohne das externe Codeverhalten zu beeinflussen.  
  
 Visual C\# stellt die folgenden Umgestaltungsbefehle im Menü **Umgestaltung** bereit:  
  
-   [Umgestaltung "Methode extrahieren" \(C\#\)](../csharp-ide/extract-method-refactoring-csharp.md)  
  
-   [Umgestaltung durch Umbenennen \(C\#\)](../csharp-ide/rename-refactoring-csharp.md)  
  
-   [Encapsulate Field Refactoring \(C\#\)](../csharp-ide/encapsulate-field-refactoring-csharp.md)  
  
-   [Extract Interface Refactoring \(C\#\)](../csharp-ide/extract-interface-refactoring-csharp.md)  
  
-   [Umgestaltung "Parameter entfernen" \(C\#\)](../csharp-ide/remove-parameters-refactoring-csharp.md)  
  
-   [Reorder Parameters Refactoring \(C\#\)](../csharp-ide/reorder-parameters-refactoring-csharp.md)  
  
## Umgestaltung mehrerer Projekte  
 Visual Studio unterstützt die Umgestaltung mehrerer Projekte, wenn sich die Projekte in der gleichen Lösung befinden.  Bei allen Umgestaltungsvorgängen, durch die Verweise dateiübergreifend korrigiert werden, werden diese Verweise auch projektübergreifend für alle Projekte in derselben Programmiersprache korrigiert.  Dies funktioniert für alle Verweise von Projekt zu Projekt.  Wenn Sie beispielsweise über eine Konsolenanwendung verfügen, die auf eine Klassenbibliothek verweist, werden beim Umbenennen eines Typs der Klassenbibliothek \(mithilfe des Umgestaltungsvorgangs `Rename`\) auch die Verweise auf den Typ der Klassenbibliothek in der Konsolenanwendung aktualisiert.  
  
## Vorschau der Änderungen  
 Bei zahlreichen Umgestaltungsvorgängen haben Sie die Möglichkeit, vor dem endgültigen Speichern der Änderungen sämtliche Verweisänderungen zu überprüfen, die durch die Umgestaltung am Code vorgenommen würden.  Für diese Umgestaltungsvorgänge wird im Dialogfeld Umgestaltung die Option **Vorschau der Verweisänderungen** angezeigt.  Nachdem Sie diese Option aktiviert und den Umgestaltungsvorgang akzeptiert haben, wird das Dialogfeld **Vorschau der Änderungen** angezeigt.  Beachten Sie, dass das Dialogfeld **Vorschau der Änderungen** zwei Ansichten enthält.  In der unteren Ansicht wird der Code mit allen durch den Umgestaltungsvorgang vorgenommenen Verweisaktualisierungen angezeigt.  Wenn Sie im Dialogfeld **Vorschau der Änderungen** auf **Abbrechen** klicken, wird der Umgestaltungsvorgang beendet und der Code nicht geändert.  
  
## Umgestaltungswarnungen  
 Mit diesem Warnungsdialogfeld wird darauf hingewiesen, dass das betreffende Programm vom Compiler nicht vollständig interpretiert werden konnte und dass u. U. nicht alle entsprechenden Verweise vom Umgestaltungsmodul aktualisiert werden können.  Darüber hinaus können Sie in diesem Dialogfeld den Code im Dialogfeld **Vorschau der Änderungen** in der Vorschau anzeigen, bevor die Änderungen gespeichert werden.  
  
> [!NOTE]
>  Wenn eine Methode einen Syntaxfehler enthält \(der in der IDE durch eine rote wellenförmige Unterstreichung gekennzeichnet wird\), werden Verweise auf ein Element innerhalb dieser Methode vom Umgestaltungsmodul nicht aktualisiert.  Im Beispiel unten wird dieses Verhalten veranschaulicht.  
  
 Wenn Sie einen Umgestaltungsvorgang ausführen, ohne die Verweisänderungen in der Vorschau zu überprüfen, und im Programm ein Kompilierungsfehler festgestellt wird, wird dieses Warnungsdialogfeld standardmäßig in der Entwicklungsumgebung angezeigt.  
  
 Wenn Sie einen Umgestaltungsvorgang ausführen, für den **Vorschau der Verweisänderungen** aktiviert wurde, und im Programm ein Kompilierungsfehler festgestellt wird, wird in der Entwicklungsumgebung anstelle des Dialogfelds **Umgestaltungswarnung** im unteren Bereich des Dialogfelds **Vorschau der Änderungen** die folgende Warnmeldung eingeblendet:  
  
 **Das Projekt oder eine seiner Abhängigkeiten wird derzeit nicht erstellt.  Möglicherweise werden Verweise nicht aktualisiert.**  
  
 Diese Umgestaltungswarnung ist nur für Umgestaltungsvorgänge verfügbar, die die Option **Vorschau der Verweisänderungen** bereitstellen.  
  
## Fehlertolerante Umgestaltung und Ergebnisse der Verifizierung  
 Die Umgestaltung ist fehlertolerant.  Dies bedeutet, dass Sie eine Umgestaltung in einem Projekt ausführen können, das nicht erstellt werden kann.  In diesem Fall kann es jedoch vorkommen, dass mehrdeutige Verweise bei der Umgestaltung nicht ordnungsgemäß aktualisiert werden.  
  
 Das Dialogfeld **Ergebnisse der Verifizierung** kann Sie benachrichtigen, wenn Compilerfehler vom Umgestaltungsmodul erkannt werden oder wenn ermittelt wird, dass ein Umgestaltungsvorgang versehentlich bewirkt, dass ein Codeverweis eine abweichende Bindung als ursprünglich vorgesehen \(Problem bei der Neubindung\) verursacht.  
  
 Um die Funktion Ergebnisse der Verifizierung zu aktivieren, klicken Sie im Menü **Extras** auf **Optionen**.  Erweitern Sie im Dialogfeld **Optionen** die Option **Text\-Editor** und die Option **C\#**.  Klicken Sie auf **Erweitert**, und aktivieren Sie das Kontrollkästchen **Ergebnisse der Umgestaltung überprüfen**.  
  
 Das Dialogfeld **Ergebnisse der Verifizierung** unterscheidet zwischen zwei Arten von Problemen bei der Neubindung.  
  
### Verweise, deren Definition nicht mehr dem umbenannten Symbol entspricht  
 Diese Art von Problem bei der Neubindung tritt auf, wenn sich ein Verweis nicht mehr auf ein umbenanntes Symbol bezieht.  Beachten Sie z. B. folgenden Code:  
  
```c#  
class Example  
{  
    private int a;  
    public Example(int b)  
    {  
        a = b;  
    }  
}  
```  
  
 Wenn Sie die Umgestaltung verwenden, um `a` in `b` umzubenennen, wird dieses Dialogfeld angezeigt.  Der Verweis auf die umbenannte Variable `a` weist jetzt anstelle einer Bindung an das Feld eine Bindung an den Parameter auf, der an den Konstruktor übergeben wird.  
  
### Verweise, deren Definition jetzt zum umbenannten Symbol wird  
 Diese Art von Fehler bei der Neubindung tritt auf, wenn sich ein Verweis, der sich zuvor nicht auf das umbenannte Symbol bezog, jetzt auf das umbenannte Symbol bezieht.  Beachten Sie z. B. folgenden Code:  
  
```c#  
class Example  
{  
    private static void Method(object a) { }  
    private static void OtherMethod(int a) { }  
    static void Main(string[] args)  
    {  
        Method(5);  
    }  
}  
```  
  
 Wenn Sie einen Umgestaltungsvorgang verwenden, um `OtherMethod` in `Method` umzubenennen, wird dieses Dialogfeld angezeigt.  Der Verweis in `Main` bezieht sich jetzt auf die überladene Methode, die einen `int`\-Parameter akzeptiert, und nicht auf die überladene Methode, die einen `object`\-Parameter akzeptiert.  
  
## Siehe auch  
 [Using the Visual C\# Development Environment](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)   
 [Gewusst wie: Wiederherstellen von C\#\-Umgestaltungsausschnitten](../ide/how-to-restore-csharp-refactoring-snippets.md)