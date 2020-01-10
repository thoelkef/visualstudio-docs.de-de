---
title: Seite „Anwendung“, Projekt-Designer (Visual Basic) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: 8cec9fea-cd92-47ff-88dd-7c928f0b4a74
caps.latest.revision: 68
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 893647303b493ea633caf076658edbdcf0664ccc
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850840"
---
# <a name="application-page-project-designer-visual-basic"></a>Application Page, Project Designer (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legen Sie auf der Seite **Anwendung** des Projekt-Designers die Anwendungseinstellungen und -eigenschaften eines Projekts fest.

 Um auf die Seite **Anwendung** zuzugreifen, wählen Sie im **Projektmappen-Explorer** einen Projektknoten (nicht den Knoten **Projektmappen** aus. Wählen Sie dann in der Menüleiste die Option **Projekt** und dann **Eigenschaften** aus. Wenn der Projekt-Designer angezeigt wird, klicken Sie auf die Registerkarte **Anwendung**.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="general-application-settings"></a>Allgemeine Anwendungseinstellungen
 Mit den folgenden Optionen können Sie allgemeine Einstellungen für eine Anwendung konfigurieren.

 **AssemblyName** Gibt den Namen der Ausgabedatei an, die das Assemblymanifest enthält. Wenn Sie diese Eigenschaft ändern, wird auch die Eigenschaft **Ausgabename** geändert. Sie können diese Änderung auch an einer Eingabeaufforderung mit [/out (Visual Basic)](https://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae) durchführen. Informationen zum programmgesteuerten Zugreifen auf diese Eigenschaft finden Sie unter <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

 Stamm **Namespace** Gibt den Basis Namespace für alle Dateien im Projekt an. Wenn Sie beispielsweise den **Stammnamespace** auf `Project1` festgelegt haben und eine `Class1` außerhalb aller Namespaces im Code vorhanden ist, würde deren Namespace `Project1.Class1` lauten. Wäre eine `Class2` in einem Namespace `Order` im Code vorhanden ist, würde deren Namespace `Project1.Order.Class2` lauten.

 Wenn Sie den **Stammnamespace** löschen, können Sie die Namespacestruktur Ihres Projekts im Code festlegen.

> [!NOTE]
> Wenn Sie das Global-Schlüsselwort in einer [Namespaceanweisung](https://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2) verwenden, können Sie einen Namespace außerhalb des Stammnamespaces Ihres Projekts definieren. Wenn Sie den **Stammnamespace** löschen, wird der Namespace `Global` der Namespace der obersten Ebene, wodurch die Notwendigkeit entfällt, das `Global`-Schlüsselwort in einer `Namespace`-Anweisung zu verwenden. Weitere Informationen finden Sie unter „Global-Schlüsselwort in Namespace-Anweisungen“ unter [Namespaces in Visual Basic](https://msdn.microsoft.com/library/cffac744-ab8c-4f1f-ba50-732c22ab4b88).

 Informationen zum Erstellen von Namespaces im Code finden Sie unter [Namespace-Anweisung](https://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2).

 Weitere Informationen zur Stammnamespace-Eigenschaft finden Sie unter [/rootnamespace](https://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783).

 Informationen zum programmgesteuerten Zugreifen auf diese Eigenschaft finden Sie unter <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

 **Ziel Framework (alle Konfigurationen)** Gibt die Version der .NET Framework an, die die Anwendung als Ziel hat. Diese Option kann unterschiedliche Werte aufweisen, je nachdem, welche Versionen von .NET Framework auf dem Computer installiert sind.

 Der Standardwert entspricht dem Zielframework, das im Dialogfeld **Neues Projekt** angegeben wurde.

> [!NOTE]
> Die im Dialogfeld [Erforderliche Komponenten](../../ide/reference/prerequisites-dialog-box.md) aufgelisteten Pakete mit erforderlichen Komponenten werden automatisch festgelegt, wenn Sie das Dialogfeld zum ersten Mal öffnen. Wenn im Nachhinein Änderungen am Zielframework des Projekts vorgenommen werden, müssen Sie die erforderlichen Komponenten entsprechend dem neuen Zielframework manuell auswählen.

 Weitere Informationen finden Sie unter [Vorgehensweise: Bestimmte .NET Framework-Version als Ziel](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) und [Übersicht über die Ausrichtung auf mehrere Zielversionen in Visual Studio](../../ide/visual-studio-multi-targeting-overview.md).

 **Anwendungstyp**: gibt den Typ der zu erstellenden Anwendung an. Für [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]-App können Sie **Windows Store-App**, **Klassenbibliothek** oder **WinMD-Datei** angeben. Für die meisten anderen Anwendungstypen können Sie **Windows-Anwendung**, **Konsolenanwendung**, **Klassenbibliothek**, **Windows-Dienst** oder **Websteuerelementbibliothek** angeben.

 Für ein Webanwendungsprojekt müssen Sie **-Klassenbibliothek** angeben.

 Wenn Sie die Option **WinMD-Datei** angeben, können Typen in eine beliebige Windows Runtime-Programmiersprache projiziert werden. Wenn Sie die Ausgabe des Projekts als WinMD-Datei packen, können Sie eine Anwendung in mehreren Sprachen codieren und einer Interaktion der verschiedenen Codes erreichen, als ob sie in derselben Sprache geschrieben wären. Sie können die Option **WinMD-Datei** für Projektmappen verwenden, die auf Windows Runtime-Bibliotheken abzielen, beispielsweise [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]-Apps. Weitere Informationen finden Sie unter [Erstellen von Windows-Runtime-Komponenten in C# und Visual Basic](https://msdn.microsoft.com/library/windows/apps/br230301(v=VS.85).aspx).

> [!NOTE]
> Die Windows Runtime kann Typen so projizieren, dass sie unabhängig von der verwendeten Sprache als systemeigene Objekte erscheinen. Beispielsweise verwenden JavaScript-Anwendungen, die mit der Windows Runtime interagieren, diese als JavaScript-Objektsatz, und C#-Anwendungen benutzen die Bibliothek als eine Sammlung von .NET-Objekten. Wenn Sie die Ausgabe des Projekts als WinMD-Datei packen, können Sie die gleiche Technologie nutzen, die Windows Runtime verwendet.

 Weitere Informationen zur Eigenschaft **Anwendungstyp** finden Sie unter [/target (Visual Basic)](https://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c). Informationen zum programmgesteuerten Zugreifen auf diese Eigenschaft finden Sie unter <xref:VSLangProj.ProjectProperties.OutputType%2A>.

 **Symbol**: legt die ICO-Datei fest, die als Programmsymbol verwendet werden soll. Wählen Sie **\<Durchsuchen...>** aus, um nach einer vorhandenen Grafik zu suchen. Weitere Informationen finden Sie unter [/win32icon](https://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) (oder [/win32icon (C#-Compileroptionen)](https://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138)). Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

 **Start Formular/Start Objekt/Start-URI** Gibt das Start Formular oder den Einstiegspunkt der Anwendung an.

 Wenn **Anwendungsframework aktivieren** ausgewählt ist (Standard), heißt diese Liste **Startformular** und zeigt nur Formulare an, da das Anwendungsframework ausschließlich Startformulare und keine Objekte unterstützt.

 Wenn es sich bei dem Projekt um eine WPF-Browseranwendung handelt, heißt diese Liste **Start-URI**, und der Standardwert lautet **Page1.xaml**. Die Mithilfe der Liste **Start-URI** können Sie die Benutzeroberflächenressource (ein XAML-Element) angeben, die beim Start der Anwendung angezeigt wird. Weitere Informationen finden Sie unter <xref:System.Windows.Application.StartupUri%2A>.

 Wenn **Anwendungsframework aktivieren** deaktiviert ist, wird diese Liste zu **Startobjekt** und zeigt sowohl Formulare als auch Klassen oder Module mit einer `Sub Main` an.

 **Startobjekt**  definiert den Einstiegspunkt, der aufgerufen werden soll, wenn die Anwendung geladen wird. Dieser wird üblicherweise entweder auf das Hauptformular der Anwendung oder auf die `Sub Main`-Prozedur festgelegt, die beim Start der Anwendung ausgeführt werden soll. Da Klassenbibliotheken über keinen Einstiegspunkt verfügen, ist ihre einzige Option für diese Eigenschaft **(Keine)** . Weitere Informationen finden Sie unter [/main](https://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0). Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

 **Assemblyinformationen** Klicken Sie hier, um das [Dialog Feld Assemblyinformationen](../../ide/reference/assembly-information-dialog-box.md)anzuzeigen.

 **Anwendungs Framework aktivieren** Gibt an, ob ein Projekt das Anwendungs Framework verwendet. Die Einstellung dieser Option wirkt sich auf die unter **Startformular**/**Startobjekt** verfügbaren Optionen aus.

 Ist dieses Kontrollkästchen aktiviert, verwendet die Anwendung die Standard-`Sub Main`. Durch Aktivieren dieses Kontrollkästchens werden die Features im Abschnitt **Eigenschaften des Windows-Anwendungsframeworks** aktiviert, und Sie müssen ein Startformular auswählen.

 Ist dieses Kontrollkästchen deaktiviert, verwendet die Anwendung die benutzerdefinierte `Sub Main`, die Sie unter **Startformular** angegeben haben. In diesem Fall können Sie entweder ein Startobjekt (eine benutzerdefinierte `Sub Main` in einer Methode oder Klasse) oder ein Formular angeben. Außerdem sind die Optionen im Abschnitt **Eigenschaften des Windows-Anwendungsframeworks** nicht mehr verfügbar.

 **Anzeigen der Windows-Einstellungen** Klicken Sie auf diese Schaltfläche, um die Datei app. Manifest zu erstellen und zu öffnen. Visual Studio verwendet diese Datei zum Generieren von Manifestdaten für die Anwendung. Legen Sie dann die von UAC angeforderte Ausführungsebene fest, indem Sie das `<requestedExecutionLevel>`-Tag in „app.manifest“ wie folgt ändern:

 `<requestedExecutionLevel level="asInvoker" />`

 ClickOnce funktioniert mit der Ebene `asInvoker` oder im virtualisierten Modus (keine Generierung von Manifesten). Um den virtualisierten Modus anzugeben, entfernen Sie das gesamte Tag aus „app.manifest“.

 Weitere Informationen zum Generieren von Manifesten finden Sie unter [ClickOnce-Bereitstellung unter Windows Vista](../../deployment/clickonce-deployment-on-windows-vista.md).

## <a name="windows-application-framework-properties"></a>Eigenschaften des Windows-Anwendungsframeworks
 Die folgenden Einstellungen sind im Abschnitt **Eigenschaften des Windows-Anwendungsframeworks** verfügbar. Diese Optionen sind nur verfügbar, wenn das Kontrollkästchen **Anwendungsframework aktivieren** aktiviert ist. Im folgenden Abschnitt werden die **Eigenschaften des Windows-Anwendungsframeworks**-Einstellungen für Windows Presentation Foundation (WPF)-Anwendungen beschrieben.

 **Visuelle XP-Stile aktivieren** Aktiviert oder deaktiviert die visuellen Windows XP-Stile, auch bekannt als *Windows XP*-Designs. Die visuellen Windows XP-Stile aktivieren z.B. Steuerelemente mit gerundeten Ecken und dynamischen Farben. Die Option ist standardmäßig aktiviert. Weitere Informationen zu visuellen Stilen für Windows XP finden Sie unter [Windows XP-Features und Windows Forms-Steuerelemente](https://msdn.microsoft.com/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)).

 **Einzelinstanzanwendung erstellen** Aktivieren Sie dieses Kontrollkästchen, um zu verhindern, dass Benutzer mehrere Instanzen der Anwendung ausführen. Das Kontrollkästchen ist standardmäßig deaktiviert. Mit dieser Einstellung können mehrere Instanzen der Anwendung ausgeführt werden.

 **My. Settings beim Herunterfahren speichern** Aktivieren Sie dieses Kontrollkästchen, um anzugeben, dass die `My.Settings` Einstellungen der Anwendung gespeichert werden, wenn Benutzer ihre Computer Herunterfahren. Das Kontrollkästchen ist standardmäßig aktiviert. Wird diese Option deaktiviert, können Anwendungseinstellungen manuell durch Aufrufen von `My.Settings.Save` gespeichert werden.

 **Authentifizierungsmodus** Wählen Sie **Windows** (Standardeinstellung) aus, um die Verwendung der Windows-Authentifizierung anzugeben, um den derzeit angemeldeten Benutzer zu identifizieren. Sie können diese Informationen mit dem `My.User`-Objekt zur Laufzeit abrufen. Wählen Sie **Anwendungsdefiniert**, wenn Sie anstelle der standardmäßigen Windows-Authentifizierungsmethoden eigenen Code zum Authentifizieren der Benutzern bereitstellen.

 **Modus für herunter** fahren Wählen Sie **beim Schließen des Start Formulars** (Standard) aus, um anzugeben, dass die Anwendung beendet wird, wenn das als Start Formular festgelegte Formular geschlossen wird, auch wenn andere Formulare geöffnet sind. Wählen Sie **Beim Schließen des letzten Formulars** aus, um festzulegen, dass die Anwendung beendet wird, wenn das letzte Formular geschlossen oder die `My.Application.Exit`- bzw. die `End`-Anweisung explizit aufgerufen wird.

 Wählen Sie **Beim expliziten Herunterfahren** aus, um festzulegen, dass die Anwendung bei einem expliziten Aufruf von `Shutdown` beendet wird.

 Wählen Sie **Beim Schließen des letzten Fensters** aus, um festzulegen, dass die Anwendung beendet wird, wenn das letzte Fenster geschlossen oder `Shutdown` explizit aufgerufen wird. Dies ist die Standardeinstellung.

 Wählen Sie **Beim Schließen des Hauptfensters** aus, um festzulegen, dass die Anwendung beendet wird, wenn das Hauptfenster geschlossen oder `Shutdown` explizit aufgerufen wird.

 Begrüßungs **Bildschirm** Wählen Sie das Formular aus, das Sie als Begrüßungsbildschirm verwenden möchten. Sie müssen zuvor mithilfe eines Formulars oder einer Vorlage einen Begrüßungsbildschirm erstellt haben. Der Standardwert lautet **(Keine)** .

 **Anwendungs Ereignisse anzeigen** Klicken Sie auf diese Schaltfläche, um eine Ereignis Codedatei anzuzeigen, in der Sie Ereignisse für die Anwendungs Framework-Ereignisse `Startup`, `Shutdown`, `UnhandledException`, `StartupNextInstance` und `NetworkAvailabilityChanged`schreiben können. Sie können auch bestimmte Anwendungsframeworkmethoden überschreiben. Beispielsweise können Sie das Anzeigeverhalten des Begrüßungsbildschirms ändern, indem Sie `OnInitialize` überschreiben.

### <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-applications"></a>Eigenschaften des Windows-Anwendungsframeworks für Windows Presentation Foundation (WPF)-Anwendungen
 Die folgenden Einstellungen sind im Abschnitt **Eigenschaften des Windows-Anwendungsframeworks** verfügbar, wenn das Projekt eine Windows Presentation Foundation-Anwendung ist. Diese Optionen sind nur verfügbar, wenn das Kontrollkästchen **Anwendungsframework aktivieren** aktiviert ist. Die in dieser Tabelle aufgeführten Optionen sind nur für WPF-Anwendung oder WPF-Browseranwendungen verfügbar. Sie sind nicht für WPF-Benutzersteuerelement- oder benutzerdefinierte Steuerelementbibliotheken verfügbar.

 **Modus für herunter** fahren Diese Eigenschaft gilt nur für Windows Presentation Foundation Anwendungen.

 Wählen Sie **Beim expliziten Herunterfahren** aus, um festzulegen, dass die Anwendung bei einem expliziten Aufruf von <xref:System.Windows.Application.Shutdown%2A> beendet wird.

 Wählen Sie **Beim Schließen des letzten Fensters** aus, um festzulegen, dass die Anwendung beendet wird, wenn das letzte Fenster geschlossen oder <xref:System.Windows.Application.Shutdown%2A> explizit aufgerufen wird. Dies ist die Standardeinstellung.

 Wählen Sie **Beim Schließen des Hauptfensters** aus, um festzulegen, dass die Anwendung beendet wird, wenn das Hauptfenster geschlossen oder <xref:System.Windows.Application.Shutdown%2A> explizit aufgerufen wird.

 Weitere Informationen über die Verwendung diese Einstellung finden Sie unter <xref:System.Windows.Application.Shutdown%2A>.

 **XAML bearbeiten** Klicken Sie auf diese Schaltfläche, um die Anwendungs Definitionsdatei ("Application. XAML") im XAML-Editor zu öffnen und zu ändern. Wenn Sie auf diese Schaltfläche klicken, wird der Anwendungsdefinitionsknoten von „Application.xaml“ geöffnet. Möglicherweise müssen Sie diese Datei bearbeiten, um bestimmte Aufgaben auszuführen, wie z.B. das Definieren von Ressourcen. Wenn keine Anwendungsdefinitionsdatei vorhanden ist, wird sie vom Projekt-Designer erstellt.

 **Anwendungs Ereignisse anzeigen** Klicken Sie auf diese Schaltfläche, um die `Application` partielle Klassendatei ("Application. XAML. vb") in einem Code-Editor anzuzeigen. Wenn die Datei nicht vorhanden ist, wird sie vom Projekt-Designer mit dem entsprechenden Namen und Namespace erstellt.

 Das Objekt <xref:System.Windows.Application> löst Ereignisse aus, wenn bestimmte Anwendungszustandsänderungen stattfinden (z.B. beim Starten oder Herunterfahren der Anwendung). Eine vollständige Liste der Ereignisse, die diese Klasse verfügbar macht, finden Sie unter <xref:System.Windows.Application>. Diese Ereignisse werden im Benutzercodeabschnitt der partiellen `Application`-Klasse verarbeitet.

## <a name="see-also"></a>Siehe auch
[Verwalten von Anwendungseigenschaften](../../ide/application-properties.md) [Schreiben von Code in Office-Lösungen](https://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0)
