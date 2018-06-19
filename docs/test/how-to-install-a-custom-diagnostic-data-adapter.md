---
title: 'Vorgehensweise: Installieren eines benutzerdefinierten Adapters für diagnostische Daten in Visual Studio'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, installing
ms.assetid: 907e65d8-0408-44b3-9e5e-e631892c1726
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: d24ce9f954164cd8d243edfab4387f6b174c0648
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31968535"
---
# <a name="how-to-install-a-custom-diagnostic-data-adapter"></a>Gewusst wie: Installieren eines benutzerdefinierten Adapters für diagnostische Daten

Wenn Sie einen benutzerdefinierten Adapter für diagnostische Daten erstellt haben oder einen benutzerdefinierten Adapter für diagnostische Daten zur Verwendung bekommen haben, können Sie die Diagnosedatenadapter-Assembly installieren, indem Sie die Assemblydatei dafür in das richtige Verzeichnis auf dem lokalen Computer kopieren.

 Wenn Sie den benutzerdefinierten Adapter für diagnostische Daten für eine Rolle in einer Umgebung verwenden möchten, müssen Sie den Adapter für diagnostische Daten auf allen Computern installieren, auf denen für diese Rolle verwendbare Test-Agents ausgeführt werden.

 Führen Sie die folgenden Schritte aus, um den benutzerdefinierten Adapter für diagnostische Daten an den entsprechenden Speicherorten zu installieren. Sie benötigen Administratorberechtigungen für einen beliebigen Computer, auf dem Sie den Adapter für diagnostische Daten installieren.

## <a name="installing-a-custom-diagnostic-data-adapter"></a>Installieren eines benutzerdefinierten Adapters für diagnostische Daten

### <a name="to-install-a-custom-diagnostic-data-adapter"></a>So installieren Sie einen benutzerdefinierten Adapter für diagnostische Daten

1.  Um den Adapter für diagnostische Daten beim Ausführen von Tests auf dem Clientcomputer oder einem Agent-Computer zu verwenden, kopieren Sie alle Dateien aus dem Buildverzeichnis auf Grundlage des Installationspfads in das folgende Verzeichnis auf dem Zielcomputer:

     *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*

     Zu kopierende Dateien:

    -   Die Assembly des Adapters für diagnostische Daten (.dll) (erforderlich).

    -   Die Debugdatendatei (.pdb) für den Adapter (optional).

    -   Die Konfigurationsdatei für Adapter (`<diagnostic data adapter name>.dll.config`), wenn Sie standardmäßige Konfigurationseinstellungen verwenden (optional).

    -   Die Assembly des Konfigurations-Editors, wenn Sie eine Assembly erstellt haben, um die Konfigurationseinstellungen für den Adapter zu bearbeiten (optional). Dies gilt nur für Clientcomputer. Agent-Computer verwenden den Editor nicht.

    > [!NOTE]
    > Obwohl der Adapter für diagnostische Daten und der Konfigurations-Editor im gleichen Projekt erstellt und in die gleiche Assembly integriert werden können, besteht die Möglichkeit, auf Wunsch gesonderte Projekte zu verwenden und gesonderte Assemblys dafür zu erstellen.

     Weitere Informationen zum Konfigurieren der Testeinstellungen zum Verwenden einer Umgebung beim Ausführen von Tests finden Sie unter [Collect diagnostic data in manual tests (VSTS) (Sammeln von Diagnosedaten in manuellen Tests (VSTS))](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests).

2.  Sie müssen zunächst eine vorhandene Testeinstellung auswählen oder eine neue in Microsoft Test Manager oder Visual Studio erstellen, und dann müssen Sie Ihren Adapter für diagnostische Daten auf der Registerkarte **Daten und Diagnose** der ausgewählten Testeinstellungen auswählen, um den Adapter für diagnostische Daten für einen Test auszuwählen.

3.  Wenn Sie einen Konfigurations-Editor für Adapter für diagnostische Daten erstellt und installiert haben, um den Adapter für diagnostische Daten für die Testeinstellungen zu konfigurieren, klicken Sie neben dem Adapter auf **Konfigurieren**, und nehmen Sie die gewünschten Änderungen vor. Klicken Sie dann auf **Speichern**. Weitere Informationen zum Erstellen eines Konfigurations-Editors für Ihren Diagnosedatensammler finden Sie unter [How to: Create a Custom Editor for Data for Your Diagnostic Data Adapter (Vorgehensweise: Erstellen eines benutzerdefinierten Daten-Editors für den Adapter für diagnostische Daten)](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md).

4.  Wenn Sie Tests in Microsoft Test Manager ausführen, können Sie diese Testeinstellungen dem Testplan zuweisen, bevor Sie die Tests ausführen, oder verwenden Sie den Befehl **Ausführen mit Optionen**, um Testeinstellungen zuzuweisen und zu überschreiben. Weitere Informationen zu Testeinstellungen finden Sie unter [Collect Diagnostic Information Using Test Settings (Erfassen von Diagnoseinformationen mithilfe von Testeinstellungen)](../test/collect-diagnostic-information-using-test-settings.md).

     Wenn Sie die Tests aus Visual Studio ausführen, müssen Sie für diese Testeinstellungen festlegen, dass sie aktiv sind. Weitere Informationen zu Testeinstellungen finden Sie unter [Collect Diagnostic Information Using Test Settings (Erfassen von Diagnoseinformationen mithilfe von Testeinstellungen)](../test/collect-diagnostic-information-using-test-settings.md).

5.  Führen Sie die Tests unter Verwendung der Testeinstellungen aus, während der Adapter für diagnostische Daten ausgewählt ist.

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Erstellen eines Adapters für diagnostische Daten](../test/how-to-create-a-diagnostic-data-adapter.md)
- [Gewusst wie: Erstellen eines benutzerdefinierten Editors für Daten im Adapter für diagnostische Daten](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)
- [Beispielprojekt für das Erstellen eines Adapters für diagnostische Daten](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)
- [Erstellen eines Adapters für diagnostische Daten zum Sammeln von benutzerdefinierten Daten oder Beeinflussen eines Testsystems](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)
- [Collect Diagnostic Information Using Test Settings (Sammeln von Diagnoseinformationen mithilfe von Testeinstellungen)](../test/collect-diagnostic-information-using-test-settings.md)