---
title: Hinzufügen von Kontextparametern zu einer Einstellung für einen Auslastungstestlauf
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, context parameters
- load tests, context parameters
ms.assetid: a8a0b97e-8040-4711-85ab-36548b130ed2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 05efbba005a9455af3b9d2e8755b580a8af30d0a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75584477"
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>Vorgehensweise: Hinzufügen von Kontextparametern zu einer Einstellung für einen Auslastungstestlauf

Nachdem Sie den Auslastungstest mithilfe des **Assistenten für neuen Auslastungstest** erstellt haben, können Sie die Szenarioeigenschaften mit dem **Auslastungstest-Editor** entsprechend Ihren Testanforderungen und -zielen ändern.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Eine vollständige Liste der Laufzeiteinstellungseigenschaften und deren Beschreibungen finden Sie unter [Eigenschaften von Laufzeiteinstellungen für Auslastungstests](../test/load-test-run-settings-properties.md).

Sie können Kontextparameter erstellen, die in einer Auslastungstestlauf-Einstellung mit dem Auslastungstest-Editor verwendet werden sollen. Mithilfe von Kontextparametern können Sie eine Zeichenfolge parametrisieren.

Angenommen, der Auslastungstest enthält einen Webleistungstest, der bereits einen Kontextparameter einsetzt, um eine parametrisierte Webserver-URL zu verwenden. Sie können einer Auslastungstestlauf-Einstellung einen Kontextparameter hinzufügen, der den gleichen Namenswert verwendet wie der Webleistungstest. Hierdurch wird der Webleistungstest einem anderen Server zugeordnet, wenn Sie den Auslastungstest ausführen. Dies ist z. B. der Fall, wenn der Auslastungstest einen Webleistungstest einschließt, der einen Kontextparameter mit dem Namen "WebServer1" als Namen des Webservers in der URL verwendet. Wenn Sie dann in der Auslastungstestlauf-Einstellung einen Kontextparameter angeben, der ebenfalls den Namen "WebServer1" hat, verwendet der Auslastungstest den Kontextparameter, den Sie in der Auslastungstestlauf-Einstellung zugewiesen haben. Wenn der Webleistungstest im Auslastungstest also den gleichen Kontextparameternamen verwendet wie ein Kontextparameter im Auslastungstest, überschreibt der Kontextparameter im Auslastungstest den Kontextparameter, der im Webleistungstest verwendet wird.

> [!WARNING]
> Achten Sie darauf, den Kontextparameter eines Webleistungstests nicht versehentlich zu überschreiben, wenn Sie Kontextparameter in einer Testlaufeinstellung verwenden. Vermeiden Sie die Verwendung identischer Kontextparameternamen, es sei denn, dies geschieht absichtlich.

Wenn Sie `http://CorporateStagingWebServer` den Wert des Kontextparameters „Webserver1“ zuweisen, können Sie dann `WebServer1` überall im Auslastungstest verwenden und dadurch den Wert jederzeit leicht in einen anderen Webserver ändern.

Darüber hinaus können Sie den Auslastungstest mit anderen Umgebungen ausführen, indem Sie einem Kontextparameter andere Werte zuweisen, indem Sie den gleichen Namen in verschiedenen Auslastungstestlauf-Einstellungen verwenden:

- Ausführungseinstellung für Unternehmens-Stagingwebserver: Der Kontextparameter namens `WebServer1=http://CorporateStagingWebServer`

- Ausführungseinstellung „Corporate Production Web Server“: Der Kontextparameter namens `WebServer1=http://CorporateProductionWebServer`

  **Changing the Run Setting from the Command Line (Ändern der Laufzeiteinstellung über die Befehlszeile)**

  Wenn Sie in der Befehlszeile andere Testlaufeinstellungen eingeben möchten, um die Kontextparameterstrategie zu nutzen, verwenden Sie die folgenden Befehle:

  **Set Test.UseRunSetting= CorporateStagingWebServer**

  - und -

  **mstest /testcontainer:loadtest1.loadtest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>So fügen Sie einer Testlaufeinstellung einen Kontextparameter hinzu

1. Öffnen Sie einen Auslastungstest.

2. Erweitern Sie den Ordner **Laufzeiteinstellungen** in der Auslastungsteststruktur im Auslastungstest-Editor.

3. Klicken Sie mit der rechten Maustaste auf die Laufzeiteinstellung, der Sie einen Kontextparameter hinzufügen möchten, und klicken Sie dann auf **Kontextparameter hinzufügen**.

     Dem Ordner **Kontextparameter** im Ordner **Laufzeiteinstellungen** in der Auslastungsteststruktur wird ein neuer Kontextparameter hinzugefügt.

     - oder -

     Wenn die Laufzeiteinstellung bereits einen **Kontextparameter**-Ordner enthält, können Sie mit der rechten Maustaste darauf klicken und dann auf **Kontextparameter hinzufügen** klicken.

4. Ändern Sie im **Eigenschaftenfenster** den Wert für **Name** nach Bedarf (z.B. „WebServer1“). Ändern Sie im **Eigenschaftenfenster** den Parameter für **Wert** in den Parameter, den Sie verwenden möchten (z.B. `http://CorporateStagingWebServer`).

5. Optional: Wiederholen Sie die Schritte 3 bis 5, und verwenden Sie eine andere Zeichenfolge für die Eigenschaft **Wert** (z.B. `http://CorporateProductionWebServer`).

6. Wählen Sie aus, welche Ausführungseinstellungen aktiv sein sollen. Öffnen Sie das Kontextmenü in den Laufzeiteinstellungen, und wählen Sie **Als aktiv festlegen** aus.

## <a name="see-also"></a>Siehe auch

- [Konfigurieren der Laufzeiteinstellungen für Auslastungstests](../test/configure-load-test-run-settings.md)
