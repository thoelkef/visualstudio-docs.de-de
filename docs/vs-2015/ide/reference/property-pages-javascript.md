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
ms.openlocfilehash: 1fe8acd8628fcbd40e9c675558379049fd6658b8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665745"
---
# <a name="property-pages-javascript"></a>Eigenschaftenseiten, JavaScript
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die **Eigenschaftenseiten** bieten Zugriff auf die Projekteinstellungen. Sie können die Seiten, die in den **Eigenschaftenseiten** angezeigt werden, zum Ändern der Projekteigenschaften verwenden.

 Um auf die Projekteigenschaften zuzugreifen, wählen Sie im **Projektmappen-Explorer** einen Projektknoten aus. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

 Die folgenden Seiten und Optionen werden auf den **Eigenschaftenseiten** angezeigt.

## <a name="configuration-and-platform-page"></a>Konfiguration und Plattformseite
 Verwenden Sie die folgenden Optionen zum Auswählen der anzuzeigenden bzw. zu ändernden Konfiguration und Plattform.

 **Konfiguration** Gibt die Konfigurationseinstellungen an, die angezeigt oder geändert werden sollen. Die Einstellungen sind **Debuggen (Standard)** , **Release**, **Alle Konfigurationen** oder eine benutzerdefinierte Konfiguration. Weitere Informationen finden Sie unter [Debug- und Releaseprojektkonfigurationen](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Plattform** Gibt die Platt Form Einstellungen an, die angezeigt oder geändert werden sollen. Die Einstellungen sind **Beliebige CPU** (Standard für [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]-App), **x64**, **ARM**, **x86** oder eine benutzerdefinierte Plattform. Weitere Informationen finden Sie unter [Debug- und Releaseprojektkonfigurationen](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

## <a name="general-page"></a>Seite "Allgemein"
 Verwenden Sie die folgenden Optionen, um die allgemeinen Eigenschaften des Projekts festzulegen.

> [!NOTE]
> Einige Optionen sind nur für Windows Store-Apps verfügbar.

 **Ausgabepfad** Gibt den Speicherort der Ausgabedateien für die Projekt Konfiguration an. Der Pfad ist relativ. Wenn Sie einen absoluten Pfad eingeben, wird der absolute Pfad im Projekt gespeichert. Der Standardpfad ist "bin\Debug".

 Bei Verwendung vereinfachter Buildkonfigurationen bestimmt das Projektsystem, ob eine Debug- oder eine Releaseversion erstellt werden soll. Wenn Sie auf **Debuggen**, **Debuggen starten** klicken (oder F5 drücken), wird der Build unabhängig vom angegebenen **Ausgabepfad** am Speicherort für das Debuggen abgelegt. Mit dem Befehl **Projektmappe erstellen** im Menü **Erstellen** hingegen wird er an dem Speicherort abgelegt, den Sie angeben. Um erweiterte Buildkonfigurationen zu aktivieren, wählen Sie in der Menüleiste die Optionen **Extras**, **Optionen** aus. Erweitern Sie im Dialogfeld **Optionen** die Option **Projekte und Projektmappen**, wählen Sie **Allgemein** aus, und heben Sie anschließend die Markierung des Kontrollkästchens **Erweiterte Buildkonfigurationen anzeigen** auf. Dadurch erlangen Sie die manuelle Steuerung aller Konfigurationswerte, und Sie können festlegen, ob eine Debug- oder eine Releaseversion erstellt werden soll. Weitere Informationen finden Sie unter [NIB: Allgemein, Projekte und Projektmappen, Dialog Feld "Optionen](https://msdn.microsoft.com/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)".

 **Standardsprache** Gibt die Standardsprache für das Projekt an. Die Sprachenoption, die unter **Zeit, Sprache und Region** in der Systemsteuerung ausgewählt ist, gibt die bevorzugte Sprache des Benutzers an. Mit der Angabe einer Standardsprache für das Projekt kann überprüft werden, ob die angegebenen Standardsprachressourcen verwendet werden, wenn die bevorzugte Sprache des Benutzers nicht mit den in der Anwendung bereitgestellten Sprachressourcen übereinstimmt.

## <a name="debug-page"></a>Seite "Debuggen"
 Verwenden Sie die folgenden Optionen, um die Eigenschaften für das Debugverhalten im Projekt festzulegen.

> [!NOTE]
> Einige Optionen sind nur für Windows Store-Apps verfügbar.

 **Zu startender Debugger** Gibt den Standard Host für den Debugger an.

- Klicken Sie auf **Lokaler Computer**, um die Anwendung auf dem Visual Studio-Hostcomputer zu starten. Weitere Informationen finden Sie unter [Ausführen von Windows Store-Apps auf dem lokalen Computer](http://go.microsoft.com/fwlink/?LinkId=234912).

- Klicken Sie auf **Simulator**, um die Anwendung im Simulator zu starten. Weitere Informationen finden Sie unter [Ausführen von Windows Store-Apps im Simulator](http://go.microsoft.com/fwlink/?LinkId=234913).

- Klicken Sie auf **Remotecomputer**, um die Anwendung auf einem Remotecomputer zu starten. Weitere Informationen zum Remotedebuggen finden Sie unter [Ausführen von Windows Store-Apps auf einem Remotecomputer](http://go.microsoft.com/fwlink/?LinkId=234914).

  **Anwendung starten** Gibt an, ob die Anwendung gestartet werden soll, wenn Sie F5 drücken oder auf **Debuggen**, **Debugging starten**klicken. Klicken Sie auf **Ja**, um die Anwendung zu starten. Klicken Sie ansonsten auf **Nein**. Wenn Sie auf **Nein** klicken, können Sie bei Verwendung einer anderen Methode zum Starten der Anwendung diese immer noch debuggen.

  **Debuggertyp** Gibt die zu debuggenden Codetypen an. Klicken Sie auf **Nur Skript**, um JavaScript-Code zu debuggen. Klicken Sie auf **Nur verwaltet**, um Code zu debuggen, der von der Common Language Runtime verwaltet wird. Klicken Sie auf **Nur nativ**, um C++-Code zu debuggen. Klicken Sie auf **Nativ mit Skript**, um C++ und JavaScript zu debuggen. Klicken Sie auf **Gemischt (verwaltet und nativ)** aus, um sowohl verwalteten als auch C++-Code zu debuggen.

  **Lokales Netzwerk Loop Back zulassen** Gibt an, ob der Zugriff auf die IP-Loopback Adresse für App-Tests zulässig ist. Klicken Sie auf **Ja**, um die Verwendung der Loopbackadresse zuzulassen, wenn sich die Client-App auf dem gleichen Computer befindet, auf dem die Serveranwendung ausgeführt wird. Klicken Sie ansonsten auf **Nein**. Diese Eigenschaft ist nur verfügbar, wenn die Eigenschaft **Zu startender Debugger** auf **Remotecomputer** festgelegt ist.

  **Computer Name** Gibt den Namen des Remote Computers an, auf dem der Debugger gehostet wird. Diese Eigenschaft ist nur verfügbar, wenn **Zu startender Debugger** auf **Remotecomputer** festgelegt ist.

  **Authentifizierung erforderlich** Gibt an, ob der Remote Computer eine Authentifizierung erfordert. Diese Eigenschaft ist nur verfügbar, wenn **Zu startender Debugger** auf **Remotecomputer** festgelegt ist.
