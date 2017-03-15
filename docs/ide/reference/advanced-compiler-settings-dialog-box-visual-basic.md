---
title: "Dialogfeld &quot;Erweiterte Compilereinstellungen (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesAdvancedCompile"
helpviewer_keywords: 
  - "Dialogfeld "Erweiterte Compilereinstellungen""
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Dialogfeld &quot;Erweiterte Compilereinstellungen (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Verwenden Sie das Dialogfeld **Erweiterte Compilereinstellungen** des **Projekt\-Designers**, um erweiterte Eigenschaften für die Buildkonfiguration des Projekts anzugeben.  Dieses Dialogfeld gilt nur für Visual Basic\-Projekte.  
  
### So greifen Sie auf dieses Dialogfeld zu  
  
1.  In **Projektmappen\-Explorer** wählen Sie einen Projektknoten aus \(nicht den **Projektmappe** Knoten\).  
  
2.  Klicken Sie im Menü **Projekt** auf **Eigenschaften**.  Sobald der **Projekt\-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Kompilieren**.  
  
3.  Wählen Sie auf der [Seite "Kompilieren", Projekt\-Designer \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md) **Konfiguration** und **Plattform** aus.  In vereinfachten Buildkonfigurationen werden die Listen **Konfiguration** und **Plattform** nicht angezeigt.  Weitere Informationen finden Sie unter [Debug and Release Project Configurations](http://msdn.microsoft.com/de-de/0440b300-0614-4511-901a-105b771b236e).  
  
4.  Klicken Sie auf **Erweiterte Kompilierungsoptionen**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## Optimierungen  
 Die folgenden Optionen geben Optimierungen an, mit deren Hilfe in einigen Fällen eine Programmdatei verkleinert, ein Programm schneller ausgeführt oder der Buildvorgang beschleunigt werden kann.  
  
 **Überprüfungen auf Ganzzahlüberlauf entfernen**  
 Standardmäßig ist dieses Kontrollkästchen deaktiviert, um die Überprüfung des Ganzzahlüberlaufs zu aktivieren.  Aktivieren Sie dieses Kontrollkästchen, um die Überprüfung des Ganzzahlüberlaufs zu entfernen.  Wenn Sie dieses Kontrollkästchen aktivieren, werden möglicherweise ganzzahlige Berechnungen schneller.  Wenn Sie jedoch Sammelüberprüfung entfernen und Datentypkapazitäten überschreiten, werden falsche Ergebnisse ohne Fehler gespeichert werden, der ausgelöst wird.  
  
 Wenn Überlaufbedingungen und Überläufe eines der ganzen Zahl Operation überprüft werden, wird eine Ausnahme ausgelöst. <xref:System.OverflowException> Wenn Überlaufbedingungen nicht überprüft werden, lösen ganzzahlige Vorgangsüberläufe keine Ausnahme aus.  
  
 **Optimierungen aktivieren**  
 Standardmäßig ist dieses Kontrollkästchen deaktiviert, um Compileroptimierungen zu deaktivieren.  Aktivieren Sie dieses Kontrollkästchen, um Compileroptimierungen zu aktivieren.  Compileroptimierungen bewirken eine kleinere, schnellere und effizientere Ausgabedatei.  Da Optimierungsursachen\-Codeneuordnung in der Ausgabedatei Compileroptimierungen, das Debuggen erschweren kann.  
  
 **DLL\-Basisadresse**  
 Dieses Textfeld zeigt die standardmäßige DLL\-Basisadresse im Hexadezimalformat an.  In Klassenbibliotheks\- und Steuerelementbibliotheksprojekten können Sie mit diesem Textfeld die Basisadresse angeben, die beim Erstellen der DLL verwendet werden soll.  
  
 **Generieren von Debuginformationen**  
 Wählen Sie **None**, **Full** oder **pdb\-only** in der Lste aus.  **None** gibt an, dass keine Debuginformationen geniert werden.  **Full** gibt an, dass alle Debuginformationen generiert werden, und **pdb\-only** gibt an, dass nur PDB\-Debuginformationen generiert werden.  Standardmäßig ist diese Option auf **Full** festgelegt.  
  
## Kompilierungskonstanten  
 Bedingte Kompilierungskonstanten verfügen über einen Effekt, der zu dem der Anwendung [\#Const](/dotnet/visual-basic/language-reference/directives/const-directive)\-Präprozessordirektiven in einer Quelldatei entspricht, außer dass die Konstanten, die definiert werden, sind öffentlich und auf alle Dateien im Projekt.  Sie können Konstanten für die bedingte Kompilierung zusammen mit den [\#If... Then... \#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)\-Direktive verwenden, um Quelldateien bedingt zu kompilieren.  Siehe [Conditional Compilation](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).  
  
 **DEBUG\-Konstante definieren**  
 Dieses Kontrollkästchen wird standardmäßig aktiviert und gibt an, dass eine DEBUG\-Konstante festgelegt wird.  
  
 **TRACE\-Konstante definieren**  
 Dieses Kontrollkästchen wird standardmäßig aktiviert und gibt an, dass eine TRACE\-Konstante festgelegt wird.  
  
 **Benutzerdefinierte Konstanten**  
 Geben Sie alle benutzerdefinierten Konstanten für die Anwendung in dieses Textfeld ein.  Einträge sollten durch Kommas begrenzt werden, wobei dieses Format zu verwenden ist: Name1\="Wert1",Name2\="Wert2",Name3\="Wert3".  
  
## Andere Einstellungen  
 **Serialisierungsassemblys generieren**  
 Diese Einstellung gibt an, ob der Compiler XML\-Serialisierungsassemblys erstellt.  Serialisierungsassemblys können die Startleistung von <xref:System.Xml.Serialization.XmlSerializer> verbessern, sofern Sie diese Klasse zum Serialisieren von Typen im Code verwendet haben.  Standardmäßig ist diese Option auf **Auto** festgelegt, d. h. es werden nur dann Serialisierungsassemblys generiert, wenn Sie <xref:System.Xml.Serialization.XmlSerializer> verwendet haben, um Typen im Code in XML zu codieren.  **Aus** gibt an, dass grundsätzlich keine Serialisierungsassemblys generiert werden, egal ob im Code <xref:System.Xml.Serialization.XmlSerializer> verwendet wird.  **Ein** gibt an, dass immer Serialisierungsassemblys generiert werden.  Serialisierungsassemblys tragen den Namen `TypeName`.XmlSerializers.dll.  
  
## Siehe auch  
 [Seite "Kompilieren", Projekt\-Designer \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md)