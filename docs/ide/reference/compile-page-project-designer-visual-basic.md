---
title: "Seite &quot;Kompilieren&quot;, Projekt-Designer (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesCompile"
helpviewer_keywords: 
  - "Kompilierung, Visual Basic-Projekte"
  - "Kompilierung, Optionen [Visual Basic] "
  - "Compiler, Visual Basic-Optionen"
  - "Kompilierung, Anweisungen [Visual Basic] "
  - "Compileroptionen, Visual Basic"
  - "Projekt-Designer, Seite "Kompilieren""
  - "Seite "Kompilieren" im Projekt-Designer"
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
caps.latest.revision: 60
caps.handback.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Seite &quot;Kompilieren&quot;, Projekt-Designer (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Auf der Seite **Kompilieren** im Projekt\-Designer können Sie Kompilierungsanweisungen angeben.  Außerdem können Sie auf dieser Seite erweiterte Compileroptionen und Präbuild\- oder Postbuildereignisse angeben.  
  
 Um auf die Seite **Kompilieren** zuzugreifen, wählen Sie einen Projektknoten \(nicht den **Projektmappe** Knoten\) in **Projektmappen\-Explorer**.  Wählen Sie dann **Projekt**, **Eigenschaften** auf der Menüleiste aus.  Wenn der Projekt\-Designer angezeigt wird, klicken Sie auf die Registerkarte **Kompilieren**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## Konfiguration und Plattform  
 Mit den folgenden Einstellungen können Sie die anzuzeigende bzw. zu ändernde Konfiguration und Plattform auswählen.  
  
> [!NOTE]
>  Mit vereinfachten Buildkonfigurationen bestimmt das Projektsystem, ob eine Debug\- oder eine Releaseversion erstellt werden soll.  Daher werden die Listen **Konfiguration** und **Plattform** nicht angezeigt.  Weitere Informationen finden Sie unter [Debug and Release Project Configurations](http://msdn.microsoft.com/de-de/0440b300-0614-4511-901a-105b771b236e).  
  
 **Konfiguration**  
 Gibt an, welche Konfigurationseinstellungen angezeigt oder geändert werden sollen.  Die Einstellungen sind **Debug** \(Standard\), **Release** oder **Alle Konfigurationen**.  Weitere Informationen finden Sie unter [Debug and Release Project Configurations](http://msdn.microsoft.com/de-de/0440b300-0614-4511-901a-105b771b236e) und [Gewusst wie: Erstellen und Bearbeiten von Konfigurationen](../../ide/how-to-create-and-edit-configurations.md).  
  
 **Plattform**  
 Gibt an, welche Plattformeinstellungen angezeigt oder geändert werden sollen.  Sie können **Any CPU** \(Standard\), **x64** oder **x86** angeben.  Weitere Informationen finden Sie unter [Debug and Release Project Configurations](http://msdn.microsoft.com/de-de/0440b300-0614-4511-901a-105b771b236e).  
  
## Compilerkonfigurationsoptionen  
 Mit den folgenden Optionen können Sie die Compilerkonfigurationsoptionen festlegen.  
  
 **Ausgabepfad erstellen**  
 Legt den Speicherort der Ausgabedateien für die Konfiguration des Projekts fest.  Geben Sie den Pfad der Buildausgabe in dieses Feld ein, oder klicken Sie auf die Schaltfläche **Durchsuchen**, um einen Pfad auszuwählen.  Beachten Sie, dass der Pfad relativ ist. Bei der Eingabe eines absoluten Pfads wird dieser als relativer Pfad gespeichert.  Der Standardpfad lautet bin\\Debug\\ oder bin\\Release\\.  Weitere Informationen finden Sie unter [Debug and Release Project Configurations](http://msdn.microsoft.com/de-de/0440b300-0614-4511-901a-105b771b236e).  
  
 Mit vereinfachten Buildkonfigurationen bestimmt das Projektsystem, ob eine Debug\- oder eine Releaseversion erstellt werden soll.  Mit dem Befehl **Erstellen** im Menü **Debuggen** \(F5\) wird der Build unabhängig vom angegebenen **Ausgabepfad** am Debugspeicherort abgelegt.  Mit dem Befehl **Erstellen** im Menü **Erstellen** hingegen wird er an dem Speicherort abgelegt, den Sie angeben.  Weitere Informationen finden Sie unter [Debug and Release Project Configurations](http://msdn.microsoft.com/de-de/0440b300-0614-4511-901a-105b771b236e).  
  
 **Option Explicit**  
 Gibt an, ob eine implizite Deklaration von Variablen zulässig ist.  Wählen Sie **An** aus, damit explizite Variablendeklarationen erforderlich sind.  Bewirkt, dass der Compiler Fehler meldet, wenn Variablen vor der Verwendung nicht deklariert wurden.  Wenn Sie eine implizite Deklaration der Variablen wünschen, wählen Sie **Off** aus.  
  
 Diese Einstellung entspricht der [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit)\-Compileroption.  
  
 Wenn ein Quellcodedatei eine [Option Explicit Statement](/dotnet/visual-basic/language-reference/statements/option-explicit-statement) enthält, überschreibt der Wert `On` oder `Off` in der Anweisung die Einstellung **Option Explicit** auf der Seite **Kompilieren**.  
  
 Wenn Sie ein neues Projekt erstellen, wird die Einstellung **Option Explicit** auf der Seite **Kompilieren** auf den Wert der Einstellung **Option Explicit** im Dialogfeld **Optionen** festgelegt.  Um die Einstellung in diesem Dialogfeld anzuzeigen oder zu ändern, klicken Sie im Menü **Extras** auf **Optionen**.  Erweitern Sie im Dialogfeld **Optionen** die Option **Projekte und Projektmappen**, und klicken Sie dann auf **VB\-Standard**.  Die anfängliche Standardeinstellung **Option Explicit** in **VB\-Standard** ist **On**.  
  
 Das Festlegen von **Option Explicit** auf `Off` wird im Allgemeinen nicht empfohlen.  Sie könnten einen Variablennamen an einer oder mehreren Stellen falsch schreiben, was zu unerwarteten Ergebnissen führen würde, wenn das Programm ausgeführt wird.  
  
 **Option Strict**  
 Gibt an, ob eine strikte Typsemantik erzwungen wird.  Wenn **Option Strict On** ist, verursachen die folgenden Bedingungen einen Kompilierungsfehler:  
  
-   Implizite Einschränkungskonvertierungen  
  
-   Spätes Binden  
  
-   Implizite Typisierung, die zu einem `Object`\-Typ führt  
  
 Implizite Einschränkungskonvertierungsfehler treten auf, wenn eine implizite Datentypkonvertierung vorliegt, die eine einschränkende Konvertierung ist.  Weitere Informationen finden Sie unter [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) und [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions).  
  
 Ein Objekt wird spät gebunden, wenn es einer Eigenschaft oder Methode einer Variablen zugeordnet wird, für die der Typ `Object` deklariert wurde.  Weitere Informationen finden Sie unter [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement) und [Early and Late Binding](/dotnet/visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding).  
  
 Implizite Objekttypfehler treten auf, wenn ein geeigneter Typ nicht für eine deklarierte Variable abgeleitet werden kann, sodass ein Typ von `Object` abgeleitet wird.  Dies geschieht hauptsächlich, wenn Sie eine `Dim`\-Anweisung verwenden, um eine Variable zu deklarieren, ohne eine `As`\-Klausel zu verwenden, und wenn `Option Infer` deaktiviert ist.  Weitere Informationen finden Sie unter [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Option Infer Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement) und [Visual Basic Language Specification](/dotnet/visual-basic/reference/language-specification).  
  
 Diese Einstellung **Option Strict** entspricht der [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)\-Compileroption.  
  
 Wenn ein Quellcodedatei eine [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement) enthält, überschreibt der Wert `On` oder `Off` in der Anweisung die Einstellung **Option Strict** auf der Seite **Kompilieren**.  
  
 Wenn Sie ein Projekt erstellen, wird die Einstellung **Option Strict** auf der Seite **Kompilieren** auf den Wert der Einstellung **Option Strict** im Dialogfeld **Optionen** festgelegt.  Um die Einstellung in diesem Dialogfeld anzuzeigen oder zu ändern, klicken Sie im Menü **Extras** auf **Optionen**.  Erweitern Sie im Dialogfeld **Optionen** die Option **Projekte und Projektmappen**, und klicken Sie dann auf **VB\-Standard**.  Die anfängliche Standardeinstellung **Option Strict** in **VB\-Standard** ist **Off**.  
  
 **Option Strenge individuelle Warnungen.** Der Abschnitt **Warnungskonfigurationen** auf der Seite **Kompilieren** verfügt über Einstellungen, die mit den drei Bedingungen übereinstimmen, die einen Kompilierungsfehler verursachen, wenn `Option Strict` aktiviert ist.  Nachfolgend diese Einstellungen:  
  
-   **Implizite Konvertierung**  
  
-   **Späte Bindung; Aufruf könnte zur Laufzeit einen Fehler verursachen**  
  
-   **Impliziter Typ; Objekt angenommen**  
  
 Wenn Sie **Option Strict** auf **On** festlegen, werden alle drei Warnungskonfigurationseinstellungen auf **Fehler** festgelegt.  Wenn Sie **Option Strict** auf **Off** festlegen, werden alle drei Einstellungen auf **Keine** festgelegt.  
  
 Sie können jede Warnungskonfigurationseinstellung einzeln in **Keine**, **Warnung** oder **Fehler** ändern.  Wenn alle drei Warnungskonfigurationseinstellungen auf **Fehler** festgelegt sind, wird `On` im `Option strict`\-Feld angezeigt.  Wenn alle drei auf **Keine** festgelegt sind, wird `Off` in diesem Feld angezeigt.  Für jede andere Kombination dieser Einstellungen wird **\(benutzerdefiniert\)** angezeigt.  
  
 **Option Compare**  
 Gibt den zu verwendenden Typ des Zeichenfolgenvergleichs an.  Wählen Sie **Binär** aus, um den Compiler anzuweisen, binäre Zeichenfolgenvergleiche zu verwenden, bei denen die Groß\-\/Kleinschreibung beachtet wird.  Wählen Sie **Text** aus, um gebietsschemaspezifische Textzeichenfolgenvergleiche zu verwenden, bei denen die Groß\-\/Kleinschreibung nicht berücksichtigt wird.  
  
 Diese Einstellung entspricht der [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare)\-Compileroption.  
  
 Wenn ein Quellcodedatei eine [Option Compare Statement](/dotnet/visual-basic/language-reference/statements/option-compare-statement) enthält, überschreibt der Wert `Binary` oder `Text` in der Anweisung die Einstellung **Option Compare** auf der Seite **Kompilieren**.  
  
 Wenn Sie ein Projekt erstellen, wird die Einstellung **Option Compare** auf der Seite **Kompilieren** auf den Wert der Einstellung **Option Compare** im Dialogfeld **Optionen** festgelegt.  Um die Einstellung in diesem Dialogfeld anzuzeigen oder zu ändern, klicken Sie im Menü **Extras** auf **Optionen**.  Erweitern Sie im Dialogfeld **Optionen** die Option **Projekte und Projektmappen**, und klicken Sie dann auf **VB\-Standard**.  Die anfängliche Standardeinstellung **Option Compare** in **VB\-Standard** ist **Binär**.  
  
 **Option Infer**  
 Gibt an, ob lokaler Typrückschluss in Variablendeklarationen zulässig ist.  Wählen Sie **An** aus, um die Verwendung von lokalem Typrückschluss zu ermöglichen.  Wählen Sie **Off**, um den lokalen Datentyprückschluss zu blockieren.  
  
 Diese Einstellung entspricht der [\/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer)\-Compileroption.  
  
 Wenn ein Quellcodedatei eine [Option Infer Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement) enthält, überschreibt der Wert `On` oder `Off` in der Anweisung die Einstellung **Option Infer** auf der Seite **Kompilieren**.  
  
 Wenn Sie ein Projekt erstellen, wird die Einstellung **Option Infer** auf der Seite **Kompilieren** auf den Wert der Einstellung **Option Infer** im Dialogfeld **Optionen** festgelegt.  Um die Einstellung in diesem Dialogfeld anzuzeigen oder zu ändern, klicken Sie im Menü **Extras** auf **Optionen**.  Erweitern Sie im Dialogfeld **Optionen** die Option **Projekte und Projektmappen**, und klicken Sie dann auf **VB\-Standard**.  Die anfängliche Standardeinstellung **Option Infer** in **VB\-Standard** ist **On**.  
  
 **Ziel\-CPU**  
 Gibt den Prozessor an, für den die Ausgabedatei konfiguriert ist.  Geben Sie **x86** für jeden Intel\-kompatiblen 32\-Bit\-Prozessor, **x64** für jeden Intel\-kompatiblen 64\-Bit\-Prozessor, **ARM** für jeden ARMprozessor oder **Any CPU** an, um anzugeben, dass ein Prozessor zulässig ist.  **Any CPU** ist der Standardwert für neue Projekte, da die Anwendung ermöglicht, auf die größte Anzahl von Hardwaretypen ausgeführt werden.  
  
 Weitere Informationen finden Sie unter [\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform).  
  
 **32\-Bit bevorzugen**  
 Wenn das Kontrollkästchen **32\-Bit bevorzugen** aktiviert wird, wird die Anwendung als 32\-Bit\-Anwendung auf den 32\-Bit\- und 64\-Bit\-Versionen von Windows ausgeführt.  Andernfalls wird die Anwendung als 32\-Bit\-Anwendung auf 32\-Bit\-Versionen von Windows und unter 64\-Bit\-Versionen von Windows als 64\-Bit\-Anwendung ausgeführt.  
  
 Das Ausführen, da eine 64\-Bit\-Anwendung die Zeigergröße verdoppelt und können Kompatibilitätsprobleme mit Bibliotheken verursachen, die ausschließlich 32\-Bit sind.  Sie ist sinnvoll, eine Anwendung als 64\-Bit auszuführen, wenn dies deutlich schneller ausgeführt wird oder mehr als 4 GB Arbeitsspeicher erforderlich.  
  
 Dieses Kontrollkästchen ist nur verfügbar, wenn die folgenden Bedingungen zutreffen:  
  
-   Klicken Sie auf **Seite kompilieren** wird die Liste **Ziel\-CPU** zu **Any CPU** festgelegt.  
  
-   Klicken Sie auf **Anwendungsseite** gibt die Liste **Anwendungstyp** an, dass das Projekt eine Anwendung ist.  
  
-   Klicken Sie auf **Anwendungsseite** gibt die Liste **Zielframework** .NET Framework 4.5 an.  
  
 **Warnungskonfigurationen**  
 Diese Tabelle enthält eine Liste der Buildbedingungen und die entsprechenden Benachrichtigungsebenen **Keine**, **Warnung** oder **Fehler**.  
  
 Alle Compilerwarnungen werden während der Kompilierung standardmäßig in die Aufgabenliste aufgenommen.  Wählen Sie **Alle Warnungen deaktivieren** aus, wenn der Compiler keine Warnungen oder Fehler ausgeben soll.  Wählen Sie **\+\+\+Alle Warnungen als Fehler behandeln**, wenn der Compiler Warnungen als zu behebende Fehler behandeln soll.  
  
 **Alle Warnungen deaktivieren**  
 Gibt an, ob der Compiler Benachrichtigungen ausgeben darf, wie in der weiter vorne in diesem Dokument beschriebenen Tabelle über **Bedingungen und Benachrichtigungen** angegeben.  Dieses Kontrollkästchen ist standardmäßig aktiviert.  Aktivieren Sie dieses Kontrollkästchen, um den Compiler anzuweisen, keine Warnungen oder Fehler auszugeben.  
  
 Diese Einstellung entspricht der [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)\-Compileroption.  
  
 **Alle Warnungen als Fehler behandeln**  
 Gibt an, wie Warnungen zu behandeln sind.  Dieses Kontrollkästchen ist standardmäßig deaktiviert, damit alle Warnbenachrichtigungen auf **Warnung** festgelegt bleiben.  Aktivieren Sie dieses Kontrollkästchen, um alle Warnbenachrichtigungen in **Fehler** zu ändern.  
  
 Diese Option ist nur verfügbar, wenn **Alle Warnungen deaktivieren** deaktiviert ist.  
  
 **XML\-Dokumentationsdatei generieren**  
 Gibt an, ob Dokumentationsinformationen generiert werden sollen.  Dieses Kontrollkästchen ist standardmäßig aktiviert. Dadurch wird der Compiler angewiesen, Dokumentationsinformationen zu generieren und in eine XML\-Datei aufzunehmen.  Deaktivieren Sie dieses Kontrollkästchen, um den Compiler anzuweisen, keine Dokumentation zu erstellen.  
  
 Diese Einstellung entspricht der [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc)\-Compileroption.  
  
 **Für COM\-Interop registrieren**  
 Gibt an, ob die verwaltete Anwendung ein COM\-Objekt \(einen COM Callable Wrapper\) verfügbar macht, das einem COM\-Objekt die Interaktion mit der Anwendung ermöglicht.  
  
 Dieses Kontrollkästchen ist standardmäßig deaktiviert und gibt an, dass die Anwendung COM\-Interop nicht zulässt.  Aktivieren Sie dieses Kontrollkästchen, um COM\-Interop zuzulassen.  
  
 Diese Option ist für Windows\-Anwendungsprojekte oder Konsolenanwendungsprojekte nicht verfügbar.  
  
 **Buildereignisse**  
 Klicken Sie auf diese Schaltfläche, um auf das Dialogfeld **Buildereignisse** zuzugreifen.  Geben Sie über dieses Dialogfeld Anweisungen für Präbuild\- und Postbuildkonfigurationen für das Projekt an.  Dieses Dialogfeld gilt nur für Visual Basic\-Projekte.  Weitere Informationen finden Sie unter [Dialogfeld "Buildereignisse" \(Visual Basic\)](../../ide/reference/build-events-dialog-box-visual-basic.md).  
  
 **Erweiterte Kompilierungsoptionen**  
 Klicken Sie auf diese Schaltfläche, um auf das Dialogfeld **Erweiterte Compilereinstellungen** zuzugreifen.  Geben Sie im Dialogfeld **Erweiterte Compilereinstellungen** die Eigenschaften der erweiterten Buildkonfiguration eines Projekts an.  Dieses Dialogfeld gilt nur für Visual Basic\-Projekte.  Weitere Informationen finden Sie unter [Dialogfeld "Erweiterte Compilereinstellungen \(Visual Basic\)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).  
  
## Siehe auch  
 [Debug and Release Project Configurations](http://msdn.microsoft.com/de-de/0440b300-0614-4511-901a-105b771b236e)   
 [Managing Compilation Properties](http://msdn.microsoft.com/de-de/94308881-f10f-4caf-a729-f1028e596a2c)   
 [Gewusst wie: Festlegen von Buildereignissen \(Visual Basic\)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [Gewusst wie: Erstellen und Bearbeiten von Konfigurationen](../../ide/how-to-create-and-edit-configurations.md)