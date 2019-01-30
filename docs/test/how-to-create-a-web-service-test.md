---
title: Erstellen eines Webdiensttests
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: 227c9674434e5f49b322e614c8b8c7ffefda2128
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54964573"
---
# <a name="how-to-create-a-web-service-test"></a>Vorgehensweise: Erstellen eines Webdiensttests

Sie können Webleistungstests verwenden, um Webdienste zu testen. Sie können im **Webleistungstest-Editor** mithilfe der Optionen **Anforderung einfügen** und **Webdienstanforderung einfügen** einzelne Anforderungen anpassen, um Webdienstseiten zu suchen. Im Allgemeinen werden diese Seiten nicht in der Webanwendung angezeigt. Deshalb müssen Sie die Anforderung anpassen, um Zugriff auf diese Seiten zu erhalten.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

In den folgenden Prozeduren wird ein Webdienst verwendet, der im Commerce Starter Kit enthalten ist. Sie können ihn mit dem [ASP.NET Commerce Starter Kit](http://go.microsoft.com/fwlink/?LinkId=181469) herunterladen.

**Anforderungen**

Visual Studio Enterprise

## <a name="to-test-a-web-service"></a>So testen Sie einen Webdienst

1.  Erstellen Sie einen neuen Webleistungstest. Sobald der Browser geöffnet wird, klicken Sie auf **Beenden**.

2.  Klicken Sie im **Webleistungstest-Editor** mit der rechten Maustaste auf den Webleistungstest, und wählen Sie **Webdienstanforderung hinzufügen** aus.

3.  Geben Sie als **URL**-Eigenschaft der neuen Anforderung den Namen des Webdiensts ein, z.B. **http://localhost/storecsvs/InstantOrder.asmx**.

4.  Öffnen Sie ein neues Browserfenster, und geben Sie in der *Adressensymbolleiste* die URL der **ASMX**-Seite ein. Wählen Sie die zu testende Methode aus, und überprüfen Sie die SOAP-Meldung. Sie enthält eine `SOAPAction`.

5.  Klicken Sie im **Webleistungstest-Editor** mit der rechten Maustaste auf die Anforderung, und wählen Sie **Header hinzufügen** aus, um einen neuen Header hinzuzufügen. Geben Sie `SOAPAction` in der **Name**-Eigenschaft ein. Geben Sie in der **Wert**-Eigenschaft den in `SOAPAction` angezeigten Wert ein, beispielsweise `"http://tempuri.org/CheckStatus"`.

6.  Erweitern Sie den URL-Knoten im Editor, wählen Sie den **Zeichenfolgentext**-Knoten aus und geben Sie in das Feld **Inhaltstyp** den Wert `text/xml` ein.

7.  Kehren Sie zum Browser aus Schritt 4 zurück. Wählen Sie die XML-Komponente der SOAP-Anforderung aus der Webdienst-Beschreibungsseite aus, und kopieren Sie diese in die Zwischenablage.

8.  Der XML-Inhalt ähnelt dem folgenden Beispiel:

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
     <soap:Body>
       <CheckStatus xmlns="http://tempuri.org/">
         <userName>string</userName>
         <password>string</password>
         <orderID>int</orderID>
       </CheckStatus>
     </soap:Body>
     </soap:Envelope>
     ```

9. Kehren Sie zum **Webleistungstest-Editor** zurück. Klicken Sie in der **Zeichenfolgentext-Eigenschaft** auf die Auslassungspunkte **(…)**. Fügen Sie den Inhalt der Zwischenablage in die Eigenschaft ein.

10. Sie müssen alle Platzhalterwerte im XML-Code durch gültige Werte ersetzen, damit der Test erfolgreich ausgeführt werden kann. Im vorherigen Beispiel würden Sie die zwei Instanzen von `string` und eine Instanz von `int` ersetzen. Dieser Webdienstvorgang wird nur abgeschlossen, wenn ein registrierter Benutzer den Auftrag dazu erteilt.

11. Klicken Sie mit der rechten Maustaste auf die Webdienstanforderung, und wählen Sie die Option **QueryString-Parameter für URL hinzufügen** aus.

12. Weisen Sie dem Abfragezeichenfolgen-Parameter einen Namen und einen Wert zu. Im vorherigen Beispiel ist der Name `op` und der Wert `CheckStatus`. Dies identifiziert den auszuführenden Webdienstvorgang.

    > [!NOTE]
    > Sie können Datenbindung im SOAP-Hauptteil verwenden, um mithilfe der `{{DataSourceName.TableName.ColumnName}}`-Syntax alle Platzhalterwerte durch datengebundene Werte zu ersetzen.

13. Führen Sie den Test aus. Wählen Sie im oberen Bereich des **Webleistungstest-Ergebnisviewers** die Webdienstanforderung aus. Wählen Sie im unteren Bereich die Registerkarte „Webbrowser“ aus. Die vom Webdienst zurückgegebenen XML-Daten sowie die Ergebnisse von möglicherweise ausgeführten Vorgängen werden angezeigt.

## <a name="see-also"></a>Siehe auch

- [Erstellen von benutzerdefiniertem Code und benutzerdefinierten Plug-Ins für Auslastungstests](../test/create-custom-code-and-plug-ins-for-load-tests.md)