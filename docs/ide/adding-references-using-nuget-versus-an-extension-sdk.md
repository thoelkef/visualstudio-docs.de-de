---
title: "Hinzufügen von Referenzen mithilfe von NuGet im Vergleich zu einer SDK-Erweiterung | Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4ec453e3bec8bbca0e01d0706b43f82fb413d162
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2018
---
# <a name="adding-references-using-nuget-versus-an-extension-sdk"></a>Hinzufügen von Referenzen mithilfe von NuGet im Vergleich zu einer SDK-Erweiterung

Sie können ein Paket zum Verbrauch in Visual Studio-Projekten entweder mit der NuGet-Erweiterung für Visual Studio oder mit einem Software Development Kit (SDK) bereitstellen. In diesem Thema werden die Ähnlichkeiten und Unterschiede zwischen den beiden Vorgehensweisen beschrieben. So können Sie die für Sie geeignete Methode ermitteln.

- NuGet ist ein Open-Source-Paketverwaltungssystem, das den Prozess der Integration von Bibliotheken in eine Projektmappe vereinfacht. Weitere Informationen finden Sie in der [NuGet-Dokumentation](/nuget).

- Ein SDK ist eine Auflistung von Dateien, die von Visual Studio als einzelnes Referenzelement behandelt werden. Das Dialogfeld **Verweis-Manager** führt alle SDKs auf, die für das Projekt relevant sind, das beim Anzeigen des Dialogfelds geöffnet ist. Wenn Sie einem Projekt ein SDK hinzufügen, können Sie auf den Inhalt dieses SDK über IntelliSense, **Toolbox**, Designer, den **Objektkatalog**, MSBuild, Bereitstellung, Debuggen und Verpacken zugreifen. Weitere Informationen zu SDKs finden Sie unter [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md).

## <a name="which-mechanism-should-i-use"></a>Welche Vorgehensweise sollte ich verwenden?

Die folgende Tabelle bieten einen Vergleich zwischen den verweisenden Funktionen eines SDK und den Funktionen von NuGet.

|Funktion|SDK-Unterstützung|SDK-Hinweise|NuGet-Unterstützung|NuGet-Hinweise|
|-------------|-----------------|---------------|-------------------|-----------------|
|Bei dieser Vorgehensweise wird auf eine Entität verwiesen. Anschließend sind alle Dateien und Funktionen verfügbar.|J|Sie fügen ein SDK im Dialogfeld **Verweis-Manager** hinzu. Alle Dateien und Funktionen sind während des Entwicklungsworkflows verfügbar.|J||
|MSBuild verwendet automatisch Assemblys und Windows-Metadaten-Dateien (.winmd).|J|Verweise im SDK werden automatisch an den Compiler übergeben.|J||
|MSBuild verwendet automatisch die H- oder LIB-Dateien.|J|Die *SDKName*.props-Datei teilt Visual Studio mit, wie das Visual C++-Verzeichnis usw. für automatischen H- oder LIB-Dateiverbrauch eingerichtet wird.|N||
|MSBuild verwendet automatisch JS- oder CSS-Dateien.|J|Im **Projektmappen-Explorer** können Sie den JavaScript-SDK-Verweisknoten aufklappen, um einzelne JS- oder CSS-Dateien anzuzeigen, und anschließend `<source include/>`-Tags generieren, indem Sie diese Dateien zu den Quelldateien ziehen. Das SDK unterstützt F5 und die automatische Paketeinrichtung.|J||
|MSBuild fügt der **Toolbox** automatisch das Steuerelement hinzu.|J|Die **Toolbox** kann SDKs nutzen und Steuerelemente in den von Ihnen angegebenen Registerkarten anzeigen.|N||
|Die Vorgehensweise unterstützt das Visual Studio-Installationsprogramm für Erweiterungen (VSIX).|J|VSIX verfügt über ein spezielles Manifest und eine Logik zum Erstellen von SDK-Paketen.|J|Das VSIX-Programm kann in ein anderes Setupprogramm eingebettet werden.|
|Der **Objektkatalog** listet Verweise auf.|Y|Der **Objektkatalog** erhält die Liste der Verweise in SDKs automatisch und listet sie auf.|N||
|Dateien und Links werden dem Dialogfeld **Verweis-Manager** automatisch hinzugefügt (Hilfelinks usw. werden automatisch aufgefüllt).|J|Das Dialogfeld **Verweis-Manager** listet SDKs zusammen mit Hilfelinks und der Liste von SDK-Abhängigkeiten automatisch auf.|N|NuGet stellt ein eigenes Dialogfeld **NuGet-Pakete verwalten** bereit.|
|Der Mechanismus unterstützt mehrere Architekturen.|J|SDKs können mit mehreren Konfigurationen ausgeliefert werden. MSBuild verwendet die entsprechenden Dateien für jede Projektkonfiguration.|N||
|Der Mechanismus unterstützt mehrere Konfigurationen.|J|SDKs können mit mehreren Konfigurationen ausgeliefert werden. Abhängig von der Projektarchitektur verwendet MSBuild die entsprechenden Dateien für jede Projektarchitektur.|N||
|Mit dem Mechanismus kann angegeben werden, dass Dateien „nicht kopiert“ werden sollen.|J|Je nachdem, ob Dateien im Verzeichnis \redist oder \designtime abgelegt werden, können Sie steuern, welche Dateien in das Paket der Anwendung, die die Dateien nutzt, kopiert werden sollen.|N|Sie deklarieren, welche Dateien im das Paketmanifest kopiert werden sollen.|
|Der Inhalt wird in lokalisierten Dateien angezeigt.|J|Lokalisierte XML-Dokumenten werden automatisch in die SDKs integriert, um die Entwurfszeitumgebung zu verbessern.|N||
|MSBuild unterstützt den gleichzeitigen Verbrauch mehrerer Versionen eines SDKs.|J|Das SDK unterstützt den gleichzeitigen Verbrauch mehrerer Versionen.|N|Dies ist keine Verweiserstellung. Ihr Projekt darf jeweils nicht mehr als eine Version von NuGet-Dateien enthalten.|
|Der Mechanismus unterstützt die Angabe der anwendbaren Zielframeworks, der Visual Studio-Versionen und der Projekttypen.|J|Das Dialogfeld **Verweis-Manager** und die **Toolbox** zeigen nur die SDKs an, die für ein Projekt gelten, sodass Benutzer die entsprechenden SDKs leichter auswählen können.|Y (partiell)|Pivot ist das Zielframework. Es erfolgt kein Filtern auf der Benutzeroberfläche. Bei der Installation kann ein Fehler zurückgegeben werden.|
|Der Mechanismus unterstützt das Festlegen von Registrierungsinformationen für systemeigene WinMDs.|J|Sie können die Korrelation zwischen der WINMD-Datei und der DLL-Datei in SDKManifest.xml angeben.|N||
|Der Mechanismus unterstützt das Festlegen von Abhängigkeiten von anderen SDKs.|J|Das SDK benachrichtigt den Benutzer nur. Der Benutzer muss die Installation und die Verweiserstellung nach wie vor manuell vornehmen.|J|NuGet überträgt die Daten automatisch. Der Benutzer wird nicht benachrichtigt.|
|Der Mechanismus ist in [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]-Konzepten wie Anwendungsmanifest und Framework ID integriert.|J|Das SDK muss Konzepte übergeben, die für [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] spezifisch sind, damit das Verpacken und die F5-Funktion mit SDKs, die im [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] verfügbar sind, ordnungsgemäß funktionieren.|N||
|Der Mechanismus kann in die Pipeline zum App-Debugging für [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-Apps integriert werden.|J|Das SDK muss an [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]-spezifische Konzepte übergeben werden, damit das Verpacken und die F5-Funktion mit den im [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] verfügbaren SDKs ordnungsgemäß funktionieren.|J|NuGet-Inhalt wird Teil des Projekts. F5 muss nicht speziell berücksichtigt werden.|
|Der Mechanismus wird in Anwendungsmanifeste integriert.|J|Das SDK muss an [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]-spezifische Konzepte übergeben werden, damit das Verpacken und die F5-Funktion mit den im [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] verfügbaren SDKs ordnungsgemäß funktionieren.|J|NuGet-Inhalt wird Teil des Projekts. F5 muss nicht speziell berücksichtigt werden.|
|Der Mechanismus stellt Dateien ohne Verweis bereit (stellen Sie z. B. ein Testframework zum Ausführen von Tests von [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-Apps bereit).|J|Wenn Sie die Dateien im Ordner \redist ablegen, werden die Dateien automatisch bereitgestellt.|J||
|Der Mechanismus fügt die Plattform-SDKs automatisch der Visual Studio-IDE hinzu.|J|Wenn Sie das [!INCLUDE[win8](../debugger/includes/win8_md.md)] SDK oder das Windows Phone SDK in einem bestimmten Speicherort mit einem bestimmten Layout ablegen, wird das SDK automatisch mit allen Visual Studio-Funktionen integriert.|N||
|Der Mechanismus unterstützt einen fehlerfreien Entwicklercomputer. (Das heißt, es ist keine Installation erforderlich, und das einfache Abrufen der Quellcodeverwaltung funktioniert.)|N|Da Sie auf ein SDK verweisen, müssen Sie die Projektmappe und das SDK getrennt einchecken. Sie können das SDK von den zwei Nichtregistrierungs-Standardspeicherorten einchecken, die MSBuild beim Durchlaufen der SDKs verwendet (Details finden Sie unter [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md)). Wenn ein benutzerdefinierter Speicherort der SDKs vorhanden ist, können Sie stattdessen den folgenden Code in der Projektdatei angeben:<br /><br /> `<PropertyGroup>    <SDKReferenceDirectoryRoot>C:\MySDKs</SDKReferenceDirectoryRoot>   </PropertyGroup>`<br /><br /> Checken Sie die SDKs dann in diesen Speicherort ein.|J|Wenn Sie die Projektmappe auschecken, erkennt Visual Studio die Dateien sofort und bearbeitet sie entsprechend.|
|Sie können einer großen vorhandenen Community von Paketerstellern beitreten.|Nicht zutreffend|Die Community ist neu.|J||
|Sie können einer großen vorhandenen Community von Paketverbrauchern beitreten.|Nicht zutreffend|Die Community ist neu.|J||
|Sie können an einem Ökosystem von Partnern (benutzerdefinierte Galerien, Repositorys usw.) teilhaben.|Nicht zutreffend|Die verfügbaren Repositorys umfassen Visual Studio Marketplace, Microsoft Download Center und [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].|J||
|Der Mechanismus wird in Server mit fortlaufenden Integrationsbuilds sowohl für die Paketerstellung als auch den Paketverbrauch integriert.|J|Das SDK muss den eingecheckten Speicherort (SDKReferenceDirectoryRoot-Eigenschaft) in der Befehlszeile an MSBuild übergeben.|J||
|Der Mechanismus unterstützt stabile und Vorabveröffentlichungspaketversionen.|J|Das SDK unterstützt das Hinzufügen von Verweisen auf mehrere Versionen.|J||
|Die Mechanismus unterstützt das automatische Update von installierten Paketen.|J|Wenn es als VSIX oder Bestandteil der automatischen Visual Studio-Updates ausgeliefert wird, bietet das SDK automatische Benachrichtigungen.|J||
|Der Mechanismus enthält eine eigenständige EXE-Datei zum Erstellen und Nutzen von Paketen.|J|Das SDK enthält MSBuild.exe.|J||
|Pakete können in die Versionskontrolle eingecheckt werden.|J|Sie können keine Elemente außerhalb des Knotens „Dokumente“ einchecken, d.h., dass die Erweiterungs-SDKs möglicherweise nicht eingecheckt werden. Das Erweiterungs-SDK kann sehr groß sein.|J||
|Sie können eine PowerShell-Schnittstelle verwenden, um Pakete zu erstellen und zu nutzen.|J (Verbrauch), N (Erstellung)|Keine Werkzeugausstattung zum Erstellen eines SDK. Durch den Verbrauch wird MSBuild in der Befehlszeile ausgeführt.|J||
|Sie können ein Symbolpaket für die Debugunterstützung verwenden.|J|Wenn Sie PDB-Dateien im SDK ablegen, werden die Dateien automatisch ausgewählt.|J||
|Der Mechanismus unterstützt automatische Paketmanagerupdates.|Nicht zutreffend|Das SDK wird mit MSBuild überarbeitet.|J||
|Der Mechanismus unterstützt ein einfaches Manifestformat.|J|SDKManifest.xml unterstützt viele Attribute. Normalerweise ist eine kleine Teilmenge erforderlich.|J||
|Der Mechanismus ist für alle Visual Studio-Editionen verfügbar.|J|Das SDK unterstützt alle Visual Studio-Editionen, von Visual Studio Express bis [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)].|J|NuGet unterstützt alle Visual Studio-Editionen, von Express bis [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)].|
|Der Mechanismus ist für alle Projekttypen verfügbar.|N|Das SDK unterstützt [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-Apps, die in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] beginnen.|N|Sie können eine Liste von zulässigen Projekte anzeigen.|

## <a name="see-also"></a>Siehe auch

[Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)