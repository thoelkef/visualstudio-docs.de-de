---
title: 'Vorgehensweise: Erstellen von Dateizuordnungen für eine ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 0cfdbb9262f9a70f3f680554f562ff6c5c2380b5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520712"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Gewusst wie: Erstellen von Dateizuordnungen für eine ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Erstellen Sie Datei Zuordnungen für eine ClickOnce-Anwendung](https://docs.microsoft.com/visualstudio/deployment/how-to-create-file-associations-for-a-clickonce-application).  
  
[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungen können eine oder mehrere Dateierweiterungen zugeordnet sein, damit die Anwendung automatisch gestartet wird, wenn der Benutzer eine Datei mit diesen Typen wird geöffnet. Hinzufügen von Unterstützung für Dateinamen-Erweiterung auf einem [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung ist einfach.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Zum Erstellen von dateizuordnungen für eine ClickOnce-Anwendung  
  
1.  Erstellen einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung normal, oder verwenden Sie die vorhandene [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung.  
  
2.  Öffnen Sie das Anwendungsmanifest mit einem Text- oder XML-Editor wie Editor.  
  
3.  Suchen Sie das `assembly`-Element. Weitere Informationen finden Sie unter [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md).  
  
4.  Als untergeordnetes Element der `assembly` -Element, Hinzufügen einer `fileAssociation` Element. Die `fileAssociation` Element verfügt über vier Attribute:  
  
    -   `extension`: Die Dateinamenerweiterung, die Sie der Anwendung zuordnen möchten.  
  
    -   `description`: Eine Beschreibung des Dateityps, die in der Windows-Shell angezeigt wird.  
  
    -   `progid`: Eine Zeichenfolge, die den Dateityp aus, um es in der Registrierung markieren eindeutig identifiziert.  
  
    -   `defaultIcon`: Ein Symbol für diesen Dateityp verwendet werden soll. Das Symbol muss als eine Ressource im Manifest Anwendung hinzugefügt werden. Weitere Informationen finden Sie unter [Gewusst wie: Einschließen einer Datendatei in eine ClickOnce-Anwendung](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Ein Beispiel für die `file` und `fileAssociation` Elemente finden Sie unter [ \<FileAssociation >-Element](../deployment/fileassociation-element-clickonce-application.md).  
  
5.  Wenn Sie die Anwendung mehr als einen Dateityp zuordnen möchten, fügen Sie zusätzliche `fileAssociation` Elemente. Beachten Sie, dass die `progid` Attribut sollte unterschiedlich sein.  
  
6.  Sobald Sie mit dem Anwendungsmanifest abgeschlossen haben, Signieren Sie das Manifest erneut. Sie können über die Befehlszeile dazu verwenden Mage.exe.  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     Weitere Informationen finden Sie unter [Mage.exe (Manifest Generation and Editing Tool)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)  
  
## <a name="see-also"></a>Siehe auch  
 [\<FileAssociation >-Element](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce Application Manifest (ClickOnce-Anwendungsmanifest)](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (Tool zum Generieren und Bearbeiten von Manifesten)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)



