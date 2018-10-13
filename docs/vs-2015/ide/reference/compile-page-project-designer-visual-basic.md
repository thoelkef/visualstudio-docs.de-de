---
title: Seite „Kompilieren“, Projekt-Designer (Visual Basic) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesCompile
helpviewer_keywords:
- compilation, Visual Basic projects
- compilation, options [Visual Basic]
- compilers, Visual Basic options
- compilation, instructions [Visual Basic]
- compiler options, Visual Basic
- Project Designer, Compile page
- Compile page in Project Designer
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
caps.latest.revision: 65
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2c8ed6735a1038ba2bbdf3e3fffe548be47da9d2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279638"
---
# <a name="compile-page-project-designer-visual-basic"></a>Seite "Kompilieren", Projekt-Designer (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Verwenden Sie die Seite **Kompilieren** des Projekt-Designers, um Kompilieranweisungen festzulegen. Sie können auch erweiterte Compileroptionen und Präbuild- oder Postbuildereignisse auf dieser Seite angeben.  
  
 Um auf die Seite **Kompilieren** zuzugreifen, wählen Sie einen Projektknoten (nicht den Knoten **Projektmappe**) im **Projektmappen-Explorer**. Wählen Sie dann in der Menüleiste die Option **Projekt** und dann **Eigenschaften** aus. Sobald der Projekt-Designer angezeigt wird, klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="configuration-and-platform"></a>Konfiguration und Plattform  
 Die folgenden Eigenschaften ermöglichen es Ihnen, die anzuzeigende bzw. zu ändernde Konfiguration und Plattform auszuwählen.  
  
> [!NOTE]
>  Mit vereinfachten Buildkonfigurationen bestimmt das Projektsystem, ob eine Debug- oder eine Releaseversion erstellt werden soll. Deshalb werden die Listen **Konfiguration** und **Plattform** nicht angezeigt. Weitere Informationen finden Sie unter [Debug- und Releaseprojektkonfigurationen](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 **Konfiguration**  
 Gibt an, welche Konfigurationseinstellungen angezeigt oder geändert werden sollen. Die Einstellungen sind **Debuggen** (Standard), **Freigeben** oder **Alle Konfigurationen**. Weitere Informationen finden Sie unter [Debug- und Releaseprojektkonfigurationen](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e) und [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../../ide/how-to-create-and-edit-configurations.md).  
  
 **Plattform**  
 Gibt an, welche Plattformeinstellungen angezeigt oder geändert werden sollen. Sie können **Beliebige CPU** (Standard), **x64** oder **x86** angeben. Weitere Informationen finden Sie unter [Debug- und Releaseprojektkonfigurationen](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
## <a name="compiler-configuration-options"></a>Compilerkonfigurationsoptionen  
 Mithilfe der folgenden Einstellungen können Sie die Compilerkonfigurationsoptionen festlegen.  
  
 **Ausgabepfad erstellen**  
 Legt den Speicherort der Ausgabedateien für die Konfiguration des Projekts fest. Geben Sie den Pfad der Buildausgabe in dieses Feld ein, oder klicken Sie auf die Schaltfläche **Durchsuchen**, um einen Pfad auszuwählen. Beachten Sie, dass der Pfad relativ ist. Bei der Eingabe eines absoluten Pfads wird dieser als relativer Pfad gespeichert. Der Standardpfad lautet „bin\Debug\ oder bin\Release\\“. Weitere Informationen finden Sie unter [Debug- und Releaseprojektkonfigurationen](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 Mit vereinfachten Buildkonfigurationen bestimmt das Projektsystem, ob eine Debug- oder eine Releaseversion erstellt werden soll. Mit dem Befehl **Erstellen** im Menü **Debuggen** (F5) wird der Build unabhängig vom angegebenen **Ausgabepfad** am Debugspeicherort abgelegt. Mit dem Befehl **Erstellen** im Menü **Erstellen** hingegen wird er an dem Speicherort abgelegt, den Sie angeben. Weitere Informationen finden Sie unter [Debug- und Releaseprojektkonfigurationen](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 **Option Explicit**  
 Gibt an, ob implizite Deklaration von Variablen zugelassen werden. Wählen Sie **Ein**, um die explizite Variablendeklaration festzulegen. Dadurch meldet der Compiler Fehler, wenn Variablen nicht deklariert werden, bevor sie verwendet werden. Wählen Sie **Aus**, um implizite Deklaration von Variablen zuzulassen.  
  
 Diese Einstellung entspricht der Compileroption [/optionexplicit](http://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7).  
  
 Wenn eine Quellcodedatei eine [Option Explicit-Anweisung](http://msdn.microsoft.com/library/e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc) enthält, setzt der Wert `On` oder `Off` in der Anweisung die Einstellung **Option Explicit** auf der **Seite „Kompilieren“** außer Kraft.  
  
 Wenn Sie ein neues Projekt erstellen, wird die **Option Explicit**-Einstellung in der Seite **Kompilieren** auf den Wert der **Option Explicit**-Einstellung im Dialogfeld **Optionen** festgelegt. Um die Einstellung in diesem Dialogfeld anzuzeigen oder zu ändern, klicken Sie im Menü **Extras** auf **Optionen**. Erweitern Sie im Dialogfeld **Optionen** **Projekte und Lösungen**, und klicken Sie dann auf **VB Defaults**. Die ursprüngliche Standardeinstellung **Option Explicit** in **VB Defaults** ist **Ein**.  
  
 Das Festlegen der **Option Explicit** auf `Off` ist eine bewährte Methode. Sie könnten den Namen einer Variable an einem oder mehreren Orten falsch buchstabieren, wodurch unerwartete Ergebnisse auftreten würden, wenn das Programm ausgeführt wird.  
  
 **Option Strict**  
 Gibt an, ob die strikte Typsemantik erzwungen werden soll. Wenn die **Option Strict** **Ein** ist, führen die folgenden Bedingungen zu einem Kompilierzeitfehler:  
  
-   Implizite Eingrenzungskonvertierungen  
  
-   Spätes Binden  
  
-   Implizites Typisierung der Ergebnisse in einem `Object`-Typ  
  
 Implizite Eingrenzungskonvertierungsfehler treten auf, wenn eine implizite Datentypkonvertierung vorhanden ist, die eine Eingrenzungskonvertierung ist. Weitere Informationen finden Sie unter [Option Strict-Anweisung](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), [Implizite und explizite Konvertierungen](http://msdn.microsoft.com/library/77de1659-af8a-492c-967e-e7ef60ccce66) und [Erweiternde und eingrenzende Konvertierungen](http://msdn.microsoft.com/library/058c3152-6c28-4268-af44-2209e774f0bd).  
  
 Ein Objekt wird spät gebunden, wenn es einer Eigenschaft oder Methode einer Variable zugeordnet wird, für die der Typ `Object` deklariert wurde. Weitere Informationen finden Sie unter [Option Strict-Anweisung](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5) und [Frühes und spätes Binden](http://msdn.microsoft.com/library/d6ff7f1e-b94f-4205-ab8d-5cfa91758724).  
  
 Implizite Objekttypfehler treten auf, wenn ein entsprechender Typ nicht für eine deklarierte Variable hergeleitet werden kann, also wir ein Typ von `Object` hergeleitet. Dies tritt vorwiegend auf, wenn Sie eine `Dim`-Anweisung verwenden, um eine Variable ohne die Verwendung einer `As`-Klausel deklarieren und `Option Infer` deaktiviert ist. Weitere Informationen finden Sie unter [Option Strict-Anweisung](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), [Option Infer-Anweisung](http://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652) und in der [Visual Basic-Sprachspezifikation](http://msdn.microsoft.com/library/42c30017-19d0-442e-87a2-850b66ddc3df).  
  
 Die **Option Strict**-Einstellung entspricht der [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da)-Compileroption.  
  
 Wenn eine Quellcodedatei eine [Option Strict-Anweisung](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5) enthält, setzt der Wert `On` oder `Off` in der Anweisung die Einstellung **Option Strict** auf der **Seite „Kompilieren“** außer Kraft.  
  
 Wenn Sie ein Projekt erstellen, wird die **Option Strict**-Einstellung in der Seite **Kompilieren** auf den Wert der **Option Strict**-Einstellung im Dialogfeld **Optionen** festgelegt. Um die Einstellung in diesem Dialogfeld anzuzeigen oder zu ändern, klicken Sie im Menü **Extras** auf **Optionen**. Erweitern Sie im Dialogfeld **Optionen** **Projekte und Lösungen**, und klicken Sie dann auf **VB Defaults**. Die ursprüngliche Standardeinstellung **Option Strict** in **VB Defaults** ist **Ein**.  
  
 **Einzelne Option Strict-Warnungen** Der Abschnitt **Warnungskonfigurationen** auf der Seite **Kompilieren** verfügt über Einstellungen, die mit den drei Bedingungen übereinstimmen, die einen Kompilierzeitfehler auslösen, wenn `Option Strict` aktiviert ist. Die drei Einstellungen sind die folgenden:  
  
-   **Implizite Konvertierung**  
  
-   **Späte Bindung; Aufruf könnte zur Laufzeit einen Fehler verursachen**  
  
-   **Impliziter Typ; Objekt wird angenommen**  
  
 Wenn Sie **Option Strict** auf **Ein** festlegen, werden alle drei Warnungskonfigurationseinstellungen auf **Fehler** festgelegt. Wenn Sie **Option Strict** auf **Aus** festlegen werden alle drei Einstellungen auf **Keine** festgelegt.  
  
 Sie können individuell jede Warnungskonfigurationseinstellung auf **Keine**, **Warnung** oder **Fehler** festlegen. Wenn alle drei Warnungskonfigurationseinstellungen auf **Fehler** festgelegt sind, erscheint `On` im `Option strict`-Feld. Wenn alle drei Einstellungen auf **Keine** festgelegt sind, erscheint `Off` im Feld. Für jede andere Kombination dieser Einstellungen erscheint **(benutzerdefiniert)**.  
  
 **Option Compare**  
 Gibt den Typ des Zeichenfolgenvergleichs an, der verwendet werden soll. Wählen Sie **Binär** aus, um den Compiler anzuweisen, binäre Zeichenfolgenvergleiche mit Unterscheidung zwischen Groß- und Kleinschreibung zu verwenden. Wählen Sie **Text** aus, um gebietsschemaspezifische Textzeichenfolgenvergleiche ohne Berücksichtigung der Groß- und Kleinschreibung zu verwenden.  
  
 Diese Einstellung entspricht der Compileroption [/optioncompare](http://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4).  
  
 Wenn eine Quellcodedatei eine [Option Compare-Anweisung](http://msdn.microsoft.com/library/54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e) enthält, setzt der Wert `Binary` oder `Text` in der Anweisung die Einstellung **Option Compare** auf der **Seite „Kompilieren“** außer Kraft.  
  
 Wenn Sie ein Projekt erstellen, wird die **Option Compare**-Einstellung in der Seite **Kompilieren** auf den Wert der **Option Compare**-Einstellung im Dialogfeld **Optionen** festgelegt. Um die Einstellung in diesem Dialogfeld anzuzeigen oder zu ändern, klicken Sie im Menü **Extras** auf **Optionen**. Erweitern Sie im Dialogfeld **Optionen** **Projekte und Lösungen**, und klicken Sie dann auf **VB Defaults**. Die ursprüngliche Standardeinstellung **Option Compare** in **VB Defaults** ist **Binär**.  
  
 **Option Infer**  
 Gibt an, ob die Verwendung von lokalem Typrückschluss in Variablendeklarationen zulässig ist. Wählen Sie **Ein** aus, um die Verwendung des lokalen Typrückschlusses zuzulassen. Wählen Sie **Aus** aus, um den lokalen Typrückschluss zu blockieren.  
  
 Diese Einstellung entspricht der Compileroption [/optioninfer](http://msdn.microsoft.com/library/f6c09db1-0553-464a-abe3-d4510c61d6ed).  
  
 Wenn eine Quellcodedatei eine [Option Infer-Anweisung](http://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652) enthält, setzt der Wert `On` oder `Off` in der Anweisung die Einstellung **Option Infer** auf der **Seite „Kompilieren“** außer Kraft.  
  
 Wenn Sie ein neues Projekt erstellen, ist die Einstellung **Option Infer** auf der Registerkarte **Kompilieren** auf die Einstellung **Option Infer** im Textfeld **Optionen** festgelegt. Um die Einstellung in diesem Dialogfeld anzuzeigen oder zu ändern, klicken Sie im Menü **Extras** auf **Optionen**. Erweitern Sie im Dialogfeld **Optionen** **Projekte und Lösungen**, und klicken Sie dann auf **VB Defaults**. Die ursprüngliche Standardeinstellung **Option Infer** in **VB Defaults** ist **Ein**.  
  
 **Ziel-CPU**  
 Gibt den Prozessor an, für den die Ausgabedatei konfiguriert ist. Geben Sie für jeden Intel-kompatiblen 32-Bit-Prozessor **x86**, für jeden Intel-kompatiblen 64-Bit-Prozessor **x64** und für ARM-Prozessoren **ARM** oder **Any CPU** ein, um anzugeben, dass jeder Prozessor zulässig ist. **Any CPU** (Beliebige CPU) ist der Standardwert für neue Projekte, da die Anwendung hiermit auf der größten Anzahl von Hardwaretypen ausgeführt werden kann.  
  
 Weitere Informationen finden Sie unter [/platform (Visual Basic)](http://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).  
  
 **32-Bit bevorzugen**  
 Wenn das Kontrollkästchen **32-Bit bevorzugen** ausgewählt wird, wird die Anwendung auf den 32-Bit- und 64-Bit-Versionen von Windows als 32-Bit-Anwendung ausgeführt. Die Anwendung wird andernfalls auf 32-Bit-Versionen von Windows als 32-Bit-Anwendung und auf 64-Bit-Versionen von Windows als 64-Bit-Anwendung ausgeführt.  
  
 Die Ausführung als 64-Bit-Anwendung verdoppelt die Zeigergröße und kann zu Kompatibilitätsproblemen mit Bibliotheken führen, die ausschließlich eine 32-Bit-Version sind. Es macht Sinn, eine Anwendung nur als 64-Bit auszuführen, wenn die Anwendung erheblich schneller ist oder mehr als 4 GB Speicherplatz benötigt.  
  
 Dieses Kontrollkästchen ist nur verfügbar, wenn die folgenden Bedingungen zutreffen:  
  
-   Auf der Seite **Kompilieren** ist die Liste **Ziel-CPU** auf **Beliebige CPU** festgelegt.  
  
-   Auf der Seite **Anwendung** wird in der Liste **Anwendungstyp** angegeben, dass das Projekt eine Anwendung ist.  
  
-   Auf der Seite **Anwendung** ist in der Liste **Zielframework** „.NET Framework 4.5“ angegeben.  
  
 **Warnungskonfigurationen**  
 In dieser Tabelle sind Buildbedingungen und die jeweils entsprechenden Benachrichtigungsstufen **Keine**, **Warnung** oder **Fehler** aufgeführt.  
  
 Während der Kompilierung werden standardmäßig alle Compilerwarnungen der Aufgabenliste hinzugefügt. Wählen Sie **Alle Warnungen deaktivieren** aus, um den Compiler anzuweisen, keine Warnungen oder Fehler auszugeben. Wählen Sie **Alle Warnungen als Fehler behandeln**, wenn Sie möchten, dass der Compiler Warnungen als Fehler behandelt, die behoben werden müssen.  
  
 **Alle Warnungen deaktivieren**  
 Gibt an, ob der Compiler Benachrichtigungen ausgeben darf, sowie in der vorher in diesem Dokument beschriebenen Tabelle **Bedingung und Benachrichtigung** angegeben. Dieses Kontrollkästchen ist standardmäßig deaktiviert. Aktivieren Sie dieses Kontrollkästchen, um den Compiler anzuweisen, keine Warnungen oder Fehler auszugeben.  
  
 Diese Einstellung entspricht der Compileroption [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).  
  
 **Alle Warnungen als Fehler behandeln**  
 Gibt an, wie Warnungen behandelt werden müssen. In der Standardeinstellung ist dieses Kontrollkästchen deaktiviert, damit alle Warnungsbenachrichtigungen auf **Warnung** festgelegt bleiben. Aktivieren Sie dieses Kontrollkästchen, um alle Warnungsbenachrichtigungen in **Fehler** zu ändern.  
  
 Diese Option ist nur verfügbar, wenn **Alle Warnungen deaktivieren** deaktiviert ist.  
  
 **XML-Dokumentationsdatei generieren**  
 Gibt an, ob Dokumentationsiformationen generiert werden sollen. Standardmäßig ist dieses Kontrollkästchen ausgewählt und weist den Compiler an, Dokumentationsinformationen zu generieren und diese in einer XML-Datei einzuschließen. Deaktivieren Sie dieses Kontrollkästchen, um den Compiler anzuweisen, keine Dokumentation zu erstellen.  
  
 Diese Einstellung entspricht der Compileroption [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).  
  
 **Für COM-Interop registrieren**  
 Gibt an, ob Ihre verwaltete Anwendung ein COM-Objekt (einen COM Callable Wrapper) verfügbar macht, der einem COM-Objekt die Interaktion mit der verwalteten Anwendung ermöglicht.  
  
 Dieses Kontrollkästchen ist standardmäßig deaktiviert, was angibt, dass die Anwendung COM-Interop nicht zulässt. Aktivieren Sie dieses Kontrollkästchen, um COM-Interop zuzulassen.  
  
 Diese Option ist nicht für Windows-Anwendungs- und Konsolenanwendungsprojekte verfügbar.  
  
 **Buildereignisse**  
 Klicken Sie auf diese Schaltfläche, um auf das Dialogfeld **Buildereignisse** zuzugreifen. Verwenden Sie dieses Dialogfeld, um die Präbuild- und Postbuild-Konfigurationsanweisungen für das Projekt anzugeben. Dieses Dialogfeld gilt nur für Visual Basic-Projekte. Weitere Informationen finden Sie unter [Dialogfeld „Buildereignisse“ (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).  
  
 **Erweiterte Kompilierungsoptionen**  
 Klicken Sie auf diese Schaltfläche, um auf das Dialogfeld **Erweiterte Compileroptionen** zuzugreifen. Verwenden Sie das Dialogfeld **Erweiterte Compilereinstellungen**, um die erweiterten Buildkonfigurationseigenschaften des Projekts anzugeben. Dieses Dialogfeld gilt nur für Visual Basic-Projekte. Weitere Informationen finden Sie im [Dialogfeld „Erweiterte Compilereinstellungen“ (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debug- und Release-Projektkonfigurationen](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e)   
 [Verwalten von Kompilierungseigenschaften](http://msdn.microsoft.com/en-us/94308881-f10f-4caf-a729-f1028e596a2c)   
 [Vorgehensweise: Festlegen von Buildereignissen (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Visual Basic-Befehlszeilencompiler](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)   
 [Gewusst wie: Erstellen und Bearbeiten von Konfigurationen](../../ide/how-to-create-and-edit-configurations.md)



