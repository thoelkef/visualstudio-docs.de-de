---
title: 'Vorgehensweise: Erstellen von Dateizuordnungen für eine ClickOnce-Anwendung | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf60327e622f8eb32757d29051e3dce94661722d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Gewusst wie: Erstellen von Dateizuordnungen für eine ClickOnce-Anwendung
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen können eine oder mehrere Dateinamenerweiterungen zugeordnet werden, so, dass die Anwendung automatisch gestartet wird, wenn der Benutzer eine Datei des Typs geöffnet wird. Hinzufügen von Unterstützung für Dateinamen Erweiterung an eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung ist einfach.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Zum Erstellen von dateizuordnungen für eine ClickOnce-Anwendung  
  
1.  Erstellen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung normal, oder verwenden Sie die vorhandene [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.  
  
2.  Öffnen Sie das Anwendungsmanifest mit einem Text- oder XML-Editor wie Notepad.  
  
3.  Suchen Sie das `assembly`-Element. Weitere Informationen finden Sie unter [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md).  
  
4.  Als untergeordnetes Element von der `assembly` Element, Hinzufügen einer `fileAssociation` Element. Die `fileAssociation` Element verfügt über vier Attribute:  
  
    -   `extension`: Die Dateinamenerweiterung, die Sie der Anwendung zuordnen möchten.  
  
    -   `description`: Eine Beschreibung des Dateityps, die in der Windows-Shell angezeigt werden.  
  
    -   `progid`: Eine Zeichenfolge, die den Dateityp aus, um es in der Registrierung zu kennzeichnen eindeutig identifiziert.  
  
    -   `defaultIcon`: Ein Symbol für diesen Dateityp verwendet werden soll. Das Symbol "muss als eine Ressource" File "im Manifest Anwendung hinzugefügt werden. Weitere Informationen finden Sie unter [Gewusst wie: Einschließen einer Datendatei in eine ClickOnce-Anwendung](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Ein Beispiel für die `file` und `fileAssociation` Elemente finden Sie unter [ \<FileAssociation >-Element](../deployment/fileassociation-element-clickonce-application.md).  
  
5.  Wenn mehr als eine Datei mit der Anwendung zugeordnet werden sollen, fügen Sie zusätzliche `fileAssociation` Elemente. Beachten Sie, dass die `progid` Attribut sollte für jede identisch sein.  
  
6.  Nachdem Sie das Anwendungsmanifest abgeschlossen haben, melden Sie das Manifest erneut. Sie können dies über die Befehlszeile Zweck Mage.exe.  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     Weitere Informationen finden Sie unter [Mage.exe (Manifest generieren und Bearbeiten von Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)  
  
## <a name="see-also"></a>Siehe auch  
 [\<FileAssociation >-Element](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (Tool zum Generieren und Bearbeiten von Manifesten)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)