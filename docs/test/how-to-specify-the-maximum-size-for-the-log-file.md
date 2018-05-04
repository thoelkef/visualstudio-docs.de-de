---
title: Größe der Protokolldatei für Auslastungstests in Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging
ms.assetid: 417059bf-37ae-4e7a-b9b0-29bd71f1414f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 7faf5402f495eefe64000c67048bcb85c9197388
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-specify-the-maximum-size-for-the-log-file-for-load-tests"></a>Vorgehensweise: Angeben der maximalen Größe für die Protokolldatei für Auslastungstests

Standardmäßig wird die maximale Größe der für Auslastungstests verwendeten Protokolldatei auf 20 Megabyte festgelegt. Sie können diesen Wert ändern, indem Sie die dem Controllerdienst zugeordnete Konfigurationsdatei bearbeiten.

## <a name="specify-the-maximum-log-file-size-for-load-test"></a>Angeben der maximalen Protokolldateigröße für Auslastungstests

1.  Öffnen Sie die XML-Konfigurationsdatei *QTCcontroller.exe.config* im Verzeichnis „%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config“.

2.  Suchen Sie den `<add key="LogSizeLimitInMegs" value="20"/>`-Eintrag unter dem `<appSettings>`-Tag.

    ```xml
    <appSettings>
        <add key="LogSizeLimitInMegs" value="20"/>
        <add key="AgentConnectionTimeoutInSeconds" value="120"/>
        <add key="AgentSyncTimeoutInSeconds" value="300"/>
        <add key="ControllerServicePort" value="6901"/>
        <add key="ControllerUsersGroup" value="TeamTestControllerUsers"/>
        <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins"/>
        <add key="CreateTraceListener" value="no"/>
      </appSettings>
    ```

3.  Legen Sie für `value ="20"` die maximal zulässige Größe fest, die Sie für die Protokolldatei angeben möchten.

    > [!NOTE]
    > Durch die Eingabe des Werts "0" wird angegeben, dass die Größe der Protokolldatei nur durch den verfügbaren Speicherplatz auf dem Datenträger beschränkt wird.

## <a name="see-also"></a>Siehe auch

- [Ändern von Einstellungen für die Auslastungstestprotokollierung](../test/modify-load-test-logging-settings.md)
- [Konfigurieren von Ports für Testcontroller und Test-Agents](../test/configure-ports-for-test-controllers-and-test-agents.md)