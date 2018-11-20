---
title: Debuggen von UWP-apps auf Remotecomputern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/05/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 0350358c2225851619a84216c929b8d7435dc4e3
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750708"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Debuggen von UWP-apps auf Remotecomputern aus Visual Studio
  
Sie können Visual Studio ausführen, Debuggen, profilerstellung und zum Testen einer app (Universelle Windows Plattform) auf einem anderen Computer oder Gerät verwenden. Ausführen von UWP-app auf einem Remotecomputer ist besonders hilfreich, wenn Visual Studio-Computer nicht mit UWP-spezifische Funktionen wie die Fingereingabe, GeoLocation und physische Ausrichtung unterstützt. 

##  <a name="BKMK_Prerequisites"></a> Erforderliche Komponenten  

So debuggen Sie eine UWP-app auf einem Remotegerät in Visual Studio  
  
- Visual Studio-Projekt muss für das Remotedebuggen konfiguriert werden.
- Der Remotecomputer und Visual Studio-Computer müssen über ein Netzwerk verbunden oder direkt über ein USB- oder Ethernet-Kabel verbunden. Das Debugging über das Internet wird nicht unterstützt.  
- Sie müssen [Entwicklermodus aktivieren](/windows/uwp/get-started/enable-your-device-for-development) auf dem Visual Studio-Computer und dem Remotecomputer. 
- Remote-Computern müssen der Remotetools für Visual Studio ausgeführt werden. 
  - Einige Windows 10-Versionen starten, und führen die Remotetools automatisch. Andernfalls [installieren und Ausführen der Remotetools für Visual Studio](#BKMK_download).
  - Mobile für Windows 10-Geräte nicht erforderlich oder die Remoteserver-Verwaltungstools unterstützen. 

##  <a name="BKMK_ConnectVS"></a> Konfigurieren eines Visual Studio-Projekts für das Remotedebuggen
<a name="BKMK_DirectConnect"></a> Verwenden Sie das Projekt **Eigenschaften** an das Remotegerät an, um eine Verbindung herstellen. Die Einstellungen unterscheiden sich je nach Programmiersprache. 

> [!CAUTION]
> Standardmäßig legt die Eigenschaftenseite **universell (unverschlüsseltes Protokoll)** als die **Authentifizierungstyp** für Windows 10-Remoteverbindungen. Sie müssen möglicherweise festlegen **keine Authentifizierung** eine Verbindung mit dem Remotedebugger herstellen. **Universell (unverschlüsseltes Protokoll)** und **keine Authentifizierung** Protokolle verfügen über keine Netzwerksicherheit, damit zwischen der Entwicklung und den Remotecomputern übergebene Daten gefährdet ist. Wählen Sie die folgenden Authentifizierungstypen nur für vertrauenswürdige Netzwerke, die Sie nicht sicher durch bösartigen oder feindlichen Datenverkehr gefährdet sind. 
>
>Auf Wunsch **Windows-Authentifizierung** für die **Authentifizierungstyp**, Sie müssen sich auf den Remotecomputer beim Debuggen. Der Remotedebugger muss auch unter ausgeführt werden **Windows-Authentifizierung** -Modus mit dem gleichen Benutzerkonto wie auf dem Visual Studio-Computer.

###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Konfigurieren einer C# oder Visual Basic-Projekt für das Remotedebuggen  

1. Wählen Sie die C# oder Visual Basic-Projekt in Visual Studio **Projektmappen-Explorer** , und wählen Sie die **Eigenschaften** Symbol, drücken Sie **Alt** +  **Geben Sie**, oder mit der rechten Maustaste, und wählen Sie **Eigenschaften**.
  
1.  Klicken Sie auf die Registerkarte **Debuggen**.  
  
1.  Klicken Sie unter **Zielgerät**Option **Remotecomputer** für einen Remotecomputer, oder **Gerät** für ein direkt verbundene Mobile für Windows 10-Gerät.  
  
1.  Für einen Remotecomputer, geben Sie den Netzwerknamen oder die IP-Adresse in der **Remotecomputer** Feld, oder wählen **finden** , suchen Sie für das Gerät in die [Remoteverbindungen-Dialogfeld](#remote-connections). 
    
    ![Verwaltete Projekteigenschaften für Remotedebugging](../debugger/media/vsrun_managed_projprop_remote.png "verwalteten Debug-Projekteigenschaften")  
    
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Konfigurieren eines JavaScript- oder C++-Projekts für das Remotedebuggen   
  
1.  Wählen Sie das C++ oder JavaScript-Projekt in Visual Studio **Projektmappen-Explorer** , und wählen Sie die **Eigenschaften** Symbol, drücken Sie **Alt**+**EINGABETASTE** , oder mit der rechten Maustaste, und wählen Sie **Eigenschaften**.
  
1.  Wählen Sie die **Debuggen** Registerkarte.  
  
3.  Klicken Sie unter **zu startender Debugger**Option **Remotecomputer** für einen Remotecomputer, oder **Gerät** für ein direkt verbundene Mobile für Windows 10-Gerät. 
  
1.  Für eine remote-Computer eingeben, oder wählen Sie den Netzwerknamen oder die IP-Adresse in der **Computername** Feld oder die Drop nach unten, und wählen **suchen** , suchen Sie für das Gerät in die [RAS-Verbindungen (Dialogfeld) ](#remote-connections). 

    ![C++-Projekteigenschaften für das Remotedebuggen](../debugger/media/vsrun_cpp_projprop_remote.png "Debuggen von C++-Projekteigenschaften")
    
### <a name="remote-connections"></a> Verwenden Sie das Dialogfeld "Remoteverbindungen"

In der **Remoteverbindungen** (Dialogfeld), Sie können für einen bestimmten Remotecomputer-Namen oder die IP-Adresse suchen oder automatische Erkennung Verbindungen durch Auswählen des Symbols gerundet Pfeil in der Aktualisierung. Das Dialogfeld "durchsucht nur Geräte im lokalen Subnetz, die derzeit den Remotedebugger ausgeführt werden. Nicht alle Geräte erkannt werden können, der **Remoteverbindungen** Dialogfeld. 

 ![Remote-Verbindung (Dialogfeld)](../debugger/media/vsrun_selectremotedebuggerdlg.png "Dialogfeld \"Remoteverbindungen\"")  

>[!TIP]
>Wenn Sie anhand des Namens mit einem Remotegerät herstellen können, verwenden Sie die IP-Adresse. Um zu bestimmen, die IP-Adresse, auf dem Remotegerät, geben Sie **Ipconfig** in einem Befehlsfenster. Die IP-Adresse wird als **IPv4-Adresse**.  
    
## <a name="BKMK_download"></a> Herunterladen Sie und installieren Sie der Remotetools für Visual Studio

Für Visual Studio zum Debuggen von apps auf einem Remotecomputer befindet muss auf der Remotecomputer die Remotetools für Visual Studio ausgeführt werden. 

- Mobile für Windows 10-Geräte nicht erforderlich, und unterstützen die Remoteserver-Verwaltungstools. 
- Windows 10-PCs, die Ausführung des Erstellers Update (Version 1703) und höher, Windows 10 Xbox, IoT und HoloLens-Geräte Installieren der Remotetools automatisch, wenn Sie die app bereitstellen. 
- Auf Pre-creators Update Windows 10-PCs müssen Sie manuell herunterladen, installieren und werden die Remotetools auf dem Remotecomputer ausgeführt wird, bevor Sie das Debuggen starten.

**Zum Herunterladen und installieren die Remoteserver-Verwaltungstools:**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Konfiguration der Remotetools

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]  
  
##  <a name="BKMK_RunRemoteDebug"></a> Remotedebuggen von UWP-apps 

Remotedebuggen funktioniert genauso wie das lokale Debuggen die folgenden Schritte ausführen. 

1. Pre-creators Update-Versionen von Windows 10, vergewissern Sie sich auf den Remotedebugmonitor (*msvsmon.exe*) auf dem Remotegerät ausgeführt wird.  
   
1. Visual Studio-Computer, vergewissern Sie sich auf das richtige Ziel (**Remotecomputer** oder **Gerät**) neben dem grünen Pfeil auf der Symbolleiste angezeigt. 
   
1. Starten Sie das Debuggen durch Auswahl **Debuggen** > **Debuggen starten**, drücken **F5**, oder wählen Sie den grünen Pfeil auf der Symbolleiste. 
   
   Das Projekt kompiliert, klicken Sie dann bereitgestellt und gestartet wird, auf dem Remotegerät. Der Debugger hält die Ausführung an Haltepunkten an können, und Sie in, und Prozedurschritte für Code. 
   
1. Wählen Sie bei Bedarf **Debuggen** > **Debuggen beenden** , oder drücken Sie **UMSCHALT**+**F5** debugging beenden, und Schließen Sie die RemoteApp.
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Optionen für die remote-Bereitstellung](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)  
 [Testen von UWP-Apps mit Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Debuggen von UWP-Apps in Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
