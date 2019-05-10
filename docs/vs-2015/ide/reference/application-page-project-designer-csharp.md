---
title: Seite "Anwendung", Projekt-Designer (C#) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: f13701a8-4e2e-4474-9d60-bb43decbe0c1
caps.latest.revision: 61
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 43f3a1c388a7b29fe83654d89b63e3fd304ebfa0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437257"
---
# <a name="application-page-project-designer-c"></a>Seite "Anwendung", Projekt-Designer (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legen Sie auf der Seite **Anwendung** des **Projekt-Designers** die Anwendungseinstellungen und -eigenschaften des Projekts fest.  
  
 Um auf die Seite **Anwendung** zuzugreifen, wählen Sie im **Projektmappen-Explorer** einen Projektknoten (nicht den Knoten **Projektmappen** aus. Wählen Sie dann in der Menüleiste die Option **Projekt** und dann **Eigenschaften** aus. Wenn der Projekt-Designer angezeigt wird, klicken Sie auf die Registerkarte **Anwendung**.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="general-application-settings"></a>Allgemeine Anwendungseinstellungen  
 Mit den folgenden Optionen können Sie allgemeine Einstellungen für die Anwendung konfigurieren.  
  
 **Assemblyname**  
 Gibt den Namen der Ausgabedatei an, in der das Assemblymanifest enthalten ist. Durch Ändern dieser Eigenschaft wird auch die Eigenschaft **Ausgabename** geändert. Sie können diese Änderung auch mithilfe von [/out (C#-Compileroptionen)](http://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5) in der Befehlszeile vornehmen. Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.  
  
 **Standardnamespace**  
 Legt den Basisnamespace für alle Dateien fest, die dem Projekt hinzugefügt werden.  
  
 Weitere Informationen zum Erstellen von Namespaces im Code finden Sie unter [Namespace](http://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f).  
  
 Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.  
  
 **Zielframework**  
 Gibt die .NET Framework-Version an, auf die die Anwendung ausgerichtet ist. Diese Option kann unterschiedliche Werte aufweisen, je nachdem, welche Versionen von .NET Framework auf dem Computer installiert sind.  
  
 Standardmäßig entspricht der Wert dem Zielframework, das Sie im Dialogfeld **Neues Projekt** ausgewählt haben.  
  
> [!NOTE]
> Die im Dialogfeld [Erforderliche Komponenten](../../ide/reference/prerequisites-dialog-box.md) aufgelisteten Pakete mit erforderlichen Komponenten werden automatisch festgelegt, wenn Sie das Dialogfeld zum ersten Mal öffnen. Wenn im Nachhinein Änderungen am Zielframework des Projekts vorgenommen werden, müssen die erforderlichen Komponenten manuell ausgewählt werden, um dem neuen Zielframework zu entsprechen.  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Bestimmte .NET Framework-Version als Ziel](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) und [Übersicht über die Ausrichtung auf mehrere Zielversionen in Visual Studio](../../ide/visual-studio-multi-targeting-overview.md).  
  
 **Anwendungstyp**  
 Gibt den Typ der zu erstellenden Anwendung an. Für [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]-App können Sie **Windows Store-App**, **Klassenbibliothek** oder **WinMD-Datei** angeben. Für die meisten anderen Anwendungstypen können Sie **Windows-Anwendung**, **Konsolenanwendung**, **Klassenbibliothek**, **Windows-Dienst** oder **Websteuerelementbibliothek** angeben.  
  
 Für ein Webanwendungsprojekt müssen Sie **-Klassenbibliothek** angeben.  
  
 Wenn Sie die Option **WinMD-Datei** angeben, können Typen in eine beliebige Windows Runtime-Programmiersprache projiziert werden. Wenn Sie die Ausgabe des Projekts als WinMD-Datei packen, können Sie eine Anwendung in mehreren Sprachen codieren und einer Interaktion der verschiedenen Codes erreichen, als ob sie in derselben Sprache geschrieben wären. Sie können diese Option für Projektmappen festlegen, die auf Windows Runtime-Bibliotheken abzielen, beispielsweise [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]-Apps. Weitere Informationen finden Sie unter [Erstellen von Windows-Runtime-Komponenten in C# und Visual Basic](http://go.microsoft.com/fwlink/?LinkId=231895).  
  
> [!NOTE]
> Die Windows Runtime kann Typen so projizieren, dass sie unabhängig von der verwendeten Sprache als systemeigene Objekte erscheinen. Beispielsweise verwenden JavaScript-Anwendungen, die mit der Windows Runtime interagieren, diese als JavaScript-Objektsatz, und C#-Anwendungen benutzen die Bibliothek als eine Sammlung von .NET-Objekten. Wenn Sie die Ausgabe des Projekts als WinMD-Datei packen, können Sie die gleiche Technologie nutzen, die Windows Runtime verwendet.  
  
 Weitere Informationen über die Eigenschaft **Anwendungstyp** finden Sie unter [/target (C#-Compileroptionen)](http://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f). Informationen zum programmgesteuerten Zugreifen auf diese Eigenschaft finden Sie unter <xref:VSLangProj.ProjectProperties.OutputType%2A>.  
  
 **Assemblyinformationen**  
 Durch Klicken auf diese Schaltfläche wird das Dialogfeld[Assemblyinformationen](../../ide/reference/assembly-information-dialog-box.md) angezeigt.  
  
 **Startobjekt**  
 Definiert den Einstiegspunkt, der aufgerufen werden soll, wenn die Anwendung geladen wird. Dieser wird üblicherweise entweder auf das Hauptformular der Anwendung oder auf die `Main`-Prozedur festgelegt, die beim Start der Anwendung ausgeführt werden soll. Da Klassenbibliotheken über keinen Einstiegspunkt verfügen, ist ihre einzige Option für diese Eigenschaft **(Nicht festgelegt)**.  
  
 In einem WPF-Browseranwendungsprojekt ist diese Option standardmäßig **(Nicht festgelegt)**. Die andere Option ist *Projectname*.App. Bei dieser Art von Projekten müssen Sie den Start-URI so einstellen, dass beim Starten der Anwendung eine UI-Ressource geladen wird. Öffnen Sie hierfür im Projekt die Datei „Application.xaml“, und legen Sie die `StartupUri`-Eigenschaft auf eine XAML-Datei in Ihrem Projekt fest, beispielsweise „Window1.xaml“. Eine Liste der zulässigen Stammelemente finden Sie unter <xref:System.Windows.Application.StartupUri%2A>. In einer Klasse im Projekt müssen Sie auch eine `public static void Main()`-Methode definieren. Diese Klasse wird in der **Startobjekt**-Liste als *ProjectName.ClassName* angezeigt. Sie können dann die Klasse als Startobjekt auswählen.  
  
 Weitere Informationen hierzu finden Sie unter [/main (C#-Compileroptionen)](http://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049). Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:VSLangProj.ProjectProperties.StartupObject%2A>.  
  
## <a name="resources"></a>Ressourcen  
 Mit den folgenden Optionen können Sie allgemeine Einstellungen für die Anwendung konfigurieren.  
  
 **Symbol und Manifest**  
 Standardmäßig ist dieses Optionsfeld markiert, und die Optionen **Symbol** und **Manifest** sind aktiviert. Dadurch können Sie Ihr eigenes Symbol oder andere Optionen zur Generierung von Manifesten auswählen. Lassen Sie dieses Optionsfeld ausgewählt, es sei denn, Sie stellen eine Ressourcendatei für das Projekt bereit.  
  
 **Symbol**  
 Legt die ICO-Datei fest, die als Programmsymbol verwendet werden soll. Klicken Sie auf die Schaltfläche mit den Auslassungszeichen, um eine vorhandene Grafik zu suchen, oder geben Sie den Namen der gewünschten Datei ein. Weitere Informationen finden Sie unter [/win32icon (C#-Compileroptionen)](http://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138). Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.  
  
 **Manifest**  
 Aktiviert eine Manifestgenerierungsoption, wenn die Anwendung auf Windows Vista unter Benutzerkontensteuerung (UAC) ausgeführt wird. Diese Option kann die folgenden Werte aufweisen:  
  
- **Manifest mit Standardeinstellungen einbetten**. Unterstützt die normale Vorgehensweise von Visual Studio unter Windows Vista, bei der durch Einbetten der Sicherheitsinformationen in die ausführbare Datei der Anwendung angegeben wird, dass `requestedExecutionLevel` `AsInvoker` sein soll. Dies ist die Standardoption.  
  
- **Anwendung ohne Manifest erstellen**. Diese Methode wird auch als *Virtualisierung* bezeichnet. Verwenden Sie diese Option, wenn Kompatibilität mit früheren Anwendungen erforderlich ist.  
  
- **Properties\app.manifest**. Diese Option ist für Anwendungen erforderlich, die über ClickOnce oder COM ohne Registrierung bereitgestellt wurden. Wenn Sie eine Anwendung über ClickOnce-Bereitstellung veröffentlichen, wird **Manifest** automatisch auf diese Option festgelegt.  
  
  **Ressourcendatei**  
  Markieren Sie dieses Optionsfeld, wenn Sie eine Ressourcendatei für das Projekt bereitstellen. Durch Auswahl dieser Option, werden die Optionen **Symbol** und **Manifest** deaktiviert.  
  
  Geben Sie einen Pfadnamen ein, oder klicken Sie auf die Schaltfläche zum Durchsuchen (**...**), um dem Projekt eine Win32-Ressourcendatei hinzuzufügen.  
  
## <a name="see-also"></a>Siehe auch  
[Verwalten von Anwendungseigenschaften](../../ide/application-properties.md)  
 [Writing Code in Office Solutions](http://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0)
