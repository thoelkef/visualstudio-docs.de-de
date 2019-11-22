---
title: Eigenschaftenseiten, JavaScript | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- javascript.project.property.debugging.debuggertype
- javascript.project.property.debugging.requireauthentication
- javascript.project.property.outputpath
- javascript.project.property.debugging.launchapplication
- javascript.project.property.defaultlanguage
- javascript.project.property.debugging.machinename
- javascript.project.property.debugging.allowlocalnetworkloopback
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffb1298981481bde063de898dc81c02dad548888
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297823"
---
# <a name="property-pages-javascript"></a>Eigenschaftenseiten, JavaScript
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die **Eigenschaftenseiten** bieten Zugriff auf die Projekteinstellungen. Sie können die Seiten, die in den **Eigenschaftenseiten** angezeigt werden, zum Ändern der Projekteigenschaften verwenden.

 Um auf die Projekteigenschaften zuzugreifen, wählen Sie im **Projektmappen-Explorer** einen Projektknoten aus. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

 Die folgenden Seiten und Optionen werden auf den **Eigenschaftenseiten** angezeigt.

## <a name="configuration-and-platform-page"></a>Konfiguration und Plattformseite
 Verwenden Sie die folgenden Optionen zum Auswählen der anzuzeigenden bzw. zu ändernden Konfiguration und Plattform.

 **Configuration** Specifies the configuration settings to display or modify. Die Einstellungen sind **Debuggen (Standard)** , **Release**, **Alle Konfigurationen** oder eine benutzerdefinierte Konfiguration. Weitere Informationen finden Sie unter [Debug- und Releaseprojektkonfigurationen](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Platform** Specifies the platform settings to display or modify. Die Einstellungen sind **Beliebige CPU** (Standard für [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]-App), **x64**, **ARM**, **x86** oder eine benutzerdefinierte Plattform. Weitere Informationen finden Sie unter [Debug- und Releaseprojektkonfigurationen](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

## <a name="general-page"></a>Seite "Allgemein"
 Verwenden Sie die folgenden Optionen, um die allgemeinen Eigenschaften des Projekts festzulegen.

> [!NOTE]
> Einige Optionen sind nur für Windows Store-Apps verfügbar.

 **Output Path** Specifies the location of the output files for the project's configuration. Der Pfad ist relativ. Wenn Sie einen absoluten Pfad eingeben, wird der absolute Pfad im Projekt gespeichert. Der Standardpfad ist "bin\Debug".

 Bei Verwendung vereinfachter Buildkonfigurationen bestimmt das Projektsystem, ob eine Debug- oder eine Releaseversion erstellt werden soll. Wenn Sie auf **Debuggen**, **Debuggen starten** klicken (oder F5 drücken), wird der Build unabhängig vom angegebenen **Ausgabepfad** am Speicherort für das Debuggen abgelegt. Mit dem Befehl **Projektmappe erstellen** im Menü **Erstellen** hingegen wird er an dem Speicherort abgelegt, den Sie angeben. Um erweiterte Buildkonfigurationen zu aktivieren, wählen Sie in der Menüleiste die Optionen **Extras**, **Optionen** aus. Erweitern Sie im Dialogfeld **Optionen** die Option **Projekte und Projektmappen**, wählen Sie **Allgemein** aus, und heben Sie anschließend die Markierung des Kontrollkästchens **Erweiterte Buildkonfigurationen anzeigen** auf. Dadurch erlangen Sie die manuelle Steuerung aller Konfigurationswerte, und Sie können festlegen, ob eine Debug- oder eine Releaseversion erstellt werden soll. For more information, see [NIB: General, Projects and Solutions, Options Dialog Box](https://msdn.microsoft.com/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).

 **Default Language** Specifies the default language for the project. Die Sprachenoption, die unter **Zeit, Sprache und Region** in der Systemsteuerung ausgewählt ist, gibt die bevorzugte Sprache des Benutzers an. Mit der Angabe einer Standardsprache für das Projekt kann überprüft werden, ob die angegebenen Standardsprachressourcen verwendet werden, wenn die bevorzugte Sprache des Benutzers nicht mit den in der Anwendung bereitgestellten Sprachressourcen übereinstimmt.

## <a name="debug-page"></a>Seite "Debuggen"
 Verwenden Sie die folgenden Optionen, um die Eigenschaften für das Debugverhalten im Projekt festzulegen.

> [!NOTE]
> Einige Optionen sind nur für Windows Store-Apps verfügbar.

 **Debugger to Launch** Specifies the default host for the debugger.

- Klicken Sie auf **Lokaler Computer**, um die Anwendung auf dem Visual Studio-Hostcomputer zu starten. Weitere Informationen finden Sie unter [Ausführen von Windows Store-Apps auf dem lokalen Computer](https://go.microsoft.com/fwlink/?LinkId=234912).

- Klicken Sie auf **Simulator**, um die Anwendung im Simulator zu starten. Weitere Informationen finden Sie unter [Ausführen von Windows Store-Apps im Simulator](https://go.microsoft.com/fwlink/?LinkId=234913).

- Klicken Sie auf **Remotecomputer**, um die Anwendung auf einem Remotecomputer zu starten. Weitere Informationen zum Remotedebuggen finden Sie unter [Ausführen von Windows Store-Apps auf einem Remotecomputer](https://go.microsoft.com/fwlink/?LinkId=234914).

  **Launch Application** Specifies whether to start the application when you press F5 or click **Debug**, **Start Debugging**. Klicken Sie auf **Ja**, um die Anwendung zu starten. Klicken Sie ansonsten auf **Nein**. Wenn Sie auf **Nein** klicken, können Sie bei Verwendung einer anderen Methode zum Starten der Anwendung diese immer noch debuggen.

  **Debugger Type** Specifies the types of code to debug. Klicken Sie auf **Nur Skript**, um JavaScript-Code zu debuggen. Klicken Sie auf **Nur verwaltet**, um Code zu debuggen, der von der Common Language Runtime verwaltet wird. Klicken Sie auf **Nur nativ**, um C++-Code zu debuggen. Klicken Sie auf **Nativ mit Skript**, um C++ und JavaScript zu debuggen. Klicken Sie auf **Gemischt (verwaltet und nativ)** aus, um sowohl verwalteten als auch C++-Code zu debuggen.

  **Allow Local Network Loopback** Specifies whether access to the IP loopback address is allowed for app testing. Klicken Sie auf **Ja**, um die Verwendung der Loopbackadresse zuzulassen, wenn sich die Client-App auf dem gleichen Computer befindet, auf dem die Serveranwendung ausgeführt wird. Klicken Sie ansonsten auf **Nein**. Diese Eigenschaft ist nur verfügbar, wenn die Eigenschaft **Zu startender Debugger** auf **Remotecomputer** festgelegt ist.

  **Machine Name** Specifies the name of the remote computer to host the debugger. Diese Eigenschaft ist nur verfügbar, wenn **Zu startender Debugger** auf **Remotecomputer** festgelegt ist.

  **Require Authentication** Specifies whether the remote computer requires authentication. Diese Eigenschaft ist nur verfügbar, wenn **Zu startender Debugger** auf **Remotecomputer** festgelegt ist.
