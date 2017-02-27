---
title: "Eigenschaftenseiten, JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "javascript.project.property.debugging.debuggertype"
  - "javascript.project.property.debugging.requireauthentication"
  - "javascript.project.property.outputpath"
  - "javascript.project.property.debugging.launchapplication"
  - "javascript.project.property.defaultlanguage"
  - "javascript.project.property.debugging.machinename"
  - "javascript.project.property.debugging.allowlocalnetworkloopback"
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Eigenschaftenseiten, JavaScript
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die **Eigenschaftenseiten** bieten Zugriff auf die Projekteinstellungen.  Sie können die in den **Eigenschaftenseiten** angezeigt werden zum Ändern der Projekteigenschaften verwenden.  
  
 Um auf die Projekteigenschaften zuzugreifen, wählen Sie im **Projektmappen\-Explorer** einen Projektknoten aus.  Klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
 Die folgenden Seiten und Optionen werden in den **Eigenschaftenseiten** angezeigt.  
  
## Konfiguration und Plattformseite  
 Verwenden Sie die folgenden Optionen zum Auswählen der anzuzeigenden bzw. zu ändernden Konfiguration und Plattform.  
  
 **Konfiguration**  
 Gibt die anzuzeigenden bzw. zu ändernden Konfigurationseinstellungen an.  Die Einstellungen sind **Debuggen** \(Standard\), **Version**, **Alle Konfigurationen** oder eine benutzerdefinierte Konfiguration.  Weitere Informationen finden Sie unter [Debug and Release Project Configurations](http://msdn.microsoft.com/de-de/0440b300-0614-4511-901a-105b771b236e).  
  
 **Plattform**  
 Gibt die anzuzeigenden bzw. zu ändernden Plattformeinstellungen an.  Die Einstellungen sind **Beliebige CPU** \(Standard für [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)]\-App\), **x64**, **ARM**, **x86** oder eine benutzerdefinierte Plattform.  Weitere Informationen finden Sie unter [Debug and Release Project Configurations](http://msdn.microsoft.com/de-de/0440b300-0614-4511-901a-105b771b236e).  
  
## Seite "Allgemein"  
 Verwenden Sie die folgenden Optionen, um die allgemeinen Eigenschaften des Projekts festzulegen.  
  
> [!NOTE]
>  Einige Optionen sind nur für Windows Store\-Apps verfügbar.  
  
 **Ausgabepfad**  
 Legt den Speicherort der Ausgabedateien für die Konfiguration des Projekts fest.  Der Pfad ist relativ. Wenn Sie einen absoluten Pfad eingeben, wird der absolute Pfad im Projekt gespeichert.  Der Standardpfad ist "bin\\Debug".  
  
 Bei Verwendung vereinfachter Buildkonfigurationen bestimmt das Projektsystem, ob eine Debug\- oder eine Releaseversion erstellt werden soll.  Wenn Sie auf **Debuggen**, **Debuggen starten** klicken \(oder F5 drücken\), wird der Build unabhängig vom angegebenen **Ausgabepfad** im Speicherort für das Debuggen abgelegt.  Mit dem Befehl **Projektmappe erstellen** im Menü **Erstellen** hingegen wird er an dem Speicherort abgelegt, den Sie angeben.  Um erweiterte Buildkonfigurationen zu aktivieren, wählen Sie in der Menüleiste die Optionen **Tools**, **Optionen** aus.  Erweitern Sie im Dialogfeld **Optionen** die Option **Projekte und Projektmappen**, wählen Sie **Allgemein** aus, und heben Sie anschließend die Markierung des Kontrollkästchens **Erweiterte Buildkonfigurationen anzeigen** auf.  Dadurch erlangen Sie die manuelle Steuerung aller Konfigurationswerte, und Sie können festlegen, ob eine Debug\- oder eine Releaseversion erstellt werden soll.  Weitere Informationen finden Sie unter [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/de-de/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
 **Standardsprache**  
 Gibt die Standardsprache für das Projekt an.  Die Sprachenoption, die in **Zeit, Sprache und Region** in der Systemsteuerung ausgewählt ist, gibt die bevorzugte Sprache des Benutzers an.  Mit der Angabe einer Standardsprache für das Projekt kann überprüft werden, ob die angegebenen Standardsprachressourcen verwendet werden, wenn die bevorzugte Sprache des Benutzers nicht mit den in der Anwendung bereitgestellten Sprachressourcen übereinstimmt.  
  
## Seite "Debuggen"  
 Verwenden Sie die folgenden Optionen, um die Eigenschaften für das Debugverhalten im Projekt festzulegen.  
  
> [!NOTE]
>  Einige Optionen sind nur für Windows Store\-Apps verfügbar.  
  
 **Zu startender Debugger**  
 Gibt den Standardhost für den Debugger an.  
  
-   Wählen Sie **Lokaler Computer** aus, um die Anwendung auf dem Visual Studio\-Hostcomputer zu starten.  Weitere Informationen finden Sie unter [Ausführen von Apps auf dem lokalen Computer](http://go.microsoft.com/fwlink/?LinkId=234912).  
  
-   Wählen Sie **Simulator** aus, um die Anwendung im Simulator zu starten.  Weitere Informationen finden Sie unter [Ausführen von Apps im Simulator](http://go.microsoft.com/fwlink/?LinkId=234913).  
  
-   Wählen Sie **Remotecomputer** aus, um die Anwendung auf einem Remotecomputer zu starten.  Weitere Informationen zum Remotedebuggen finden Sie unter [Ausführen von Apps auf einem Remotecomputer](http://go.microsoft.com/fwlink/?LinkId=234914).  
  
 **Anwendung starten**  
 Gibt an, ob die Anwendung gestartet wird, wenn Sie F5 drücken oder auf **Debuggen**, **Debuggen starten** klicken.  Wählen Sie **Ja** aus, um die Anwendung zu starten. Andernfalls wählen Sie **Nein** aus.  Wenn Sie **Nein** auswählen, können Sie bei Verwendung einer anderen Methode zum Starten der Anwendung diese immer noch debuggen.  
  
 **Debuggertyp**  
 Gibt die zu debuggenden Codetypen an.  Wählen Sie **Nur Skript** aus, um JavaScript\-Code zu debuggen.  Wählen Sie **Nur verwaltet** aus, um Code zu debuggen, der von der Common Language Runtime verwaltet wird.  Wählen Sie **Nur systemeigen** aus, um C\+\+\-Code zu debuggen.  Wählen Sie **Systemeigen mit Skript** aus, um C\+\+ und JavaScript zu debuggen.  Wählen Sie **Gemischt \(verwaltet und systemeigen\)** aus, um sowohl verwalteten als auch C\+\+\-Code zu debuggen.  
  
 **Lokales Netzwerkloopback zulassen**  
 Gibt an, ob Zugriff auf die IP\-Loopbackadresse für App\-Tests zulässig ist.  Wählen **Ja** aus, um die Verwendung der Loopbackadresse zuzulassen, wenn sich die Client\-App auf dem gleichen Computer befindet, auf dem die Serveranwendung ausgeführt wird. Wählen Sie andernfalls **Nein** aus.  Diese Eigenschaft ist nur verfügbar, wenn die Eigenschaft **Zu startender Debugger** auf **Remotecomputer** festgelegt wird.  
  
 **Computername**  
 Gibt den Namen des Remotecomputers an, auf dem der Debugger gehostet wird.  Diese Eigenschaft ist nur verfügbar, wenn **Zu startender Debugger** auf **Remotecomputer** festgelegt wird.  
  
 **Authentifizierung erforderlich**  
 Gibt an, ob für den Remotecomputer eine Authentifizierung erforderlich ist.  Diese Eigenschaft ist nur verfügbar, wenn **Zu startender Debugger** auf **Remotecomputer** festgelegt wird.