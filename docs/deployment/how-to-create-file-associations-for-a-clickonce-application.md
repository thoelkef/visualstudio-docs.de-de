---
title: 'Vorgehensweise: Erstellen von Dateizuordnungen für eine ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0526351d2b3e2c223aacbe0e58d9ee39bd1b19c4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68924558"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Vorgehensweise: Erstellen von Dateizuordnungen für eine ClickOnce-Anwendung
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Anwendungen können mit einer oder mehreren Dateinamen Erweiterungen verknüpft werden, sodass die Anwendung automatisch gestartet wird, wenn der Benutzer eine Datei dieser Typen öffnet. Das Hinzufügen von Unterstützung für [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Dateinamen Erweiterungen zu einer Anwendung ist einfach.

### <a name="to-create-file-associations-for-a-clickonce-application"></a>So erstellen Sie Dateizuordnungen für eine ClickOnce-Anwendung

1. Erstellen Sie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] eine Anwendung in der Regel, oder [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwenden Sie die vorhandene Anwendung.

2. Öffnen Sie das Anwendungs Manifest mit einem Text-oder XML-Editor, z. b. Notepad.

3. Suchen Sie das `assembly` -Element. Weitere Informationen finden Sie unter [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md).

4. Fügen Sie ein `fileAssociation` -Element `assembly` als untergeordnetes Element des-Elements hinzu. Das `fileAssociation` -Element hat vier Attribute:

   - `extension`: Die Dateinamenerweiterung, die Sie der Anwendung zuordnen möchten.

   - `description`: Eine Beschreibung des Dateityps, der in der Windows-Shell angezeigt wird.

   - `progid`: Eine Zeichenfolge, die den Dateityp eindeutig identifiziert, um ihn in der Registrierung zu markieren.

   - `defaultIcon`: Ein Symbol, das für diesen Dateityp verwendet werden soll. Das Symbol muss als Datei Ressource im Anwendungs Manifest hinzugefügt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Einschließen einer Datendatei in eine ClickOnce-Anwendung](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

     Ein Beispiel für das- `file` Element `fileAssociation` und das- [ \<Element finden Sie unter fileAssociation >-Element](../deployment/fileassociation-element-clickonce-application.md).

5. Wenn Sie der Anwendung mehr als einen Dateityp zuordnen möchten, fügen Sie weitere `fileAssociation` Elemente hinzu. Beachten Sie, `progid` dass das Attribut für jedes-Attribut unterschiedlich sein sollte.

6. Wenn Sie mit dem Anwendungs Manifest fertig sind, Signieren Sie das Manifest erneut. Dies können Sie über die Befehlszeile mithilfe von " *Mage. exe*" tun.

    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`

    Weitere Informationen finden Sie unter [„Mage.exe“ (Tool zum Generieren und Bearbeiten von Manifesten)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="see-also"></a>Siehe auch
- [\<fileAssociation-> Element](../deployment/fileassociation-element-clickonce-application.md)
- [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)
- [Mage.exe (Tool zum Generieren und Bearbeiten von Manifesten)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)