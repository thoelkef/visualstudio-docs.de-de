---
title: 'Gewusst wie: Erstellen von Dateizuordnungen für eine ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82ffecdc719dad2f38208de00dc95438b3ff36ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697702"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Gewusst wie: Erstellen von Dateizuordnungen für eine ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungen können mit einer oder mehreren Dateinamen Erweiterungen verknüpft werden, sodass die Anwendung automatisch gestartet wird, wenn der Benutzer eine Datei dieser Typen öffnet. Das Hinzufügen von Unterstützung für Dateinamen Erweiterungen zu einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung ist einfach.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>So erstellen Sie Dateizuordnungen für eine ClickOnce-Anwendung  
  
1. Erstellen [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Sie eine Anwendung in der Regel, oder verwenden Sie die vorhandene [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung.  
  
2. Öffnen Sie das Anwendungs Manifest mit einem Text-oder XML-Editor, z. b. Notepad.  
  
3. Suchen Sie das `assembly` -Element. Weitere Informationen finden Sie unter [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md).  
  
4. Fügen Sie ein-Element als untergeordnetes Element des- `assembly` Elements hinzu `fileAssociation` . Das- `fileAssociation` Element hat vier Attribute:  
  
   - `extension`: Die Dateinamenerweiterung, die Sie der Anwendung zuordnen möchten.  
  
   - `description`: Eine Beschreibung des Dateityps, der in der Windows-Shell angezeigt wird.  
  
   - `progid`: Eine Zeichenfolge, die den Dateityp eindeutig identifiziert, um ihn in der Registrierung zu markieren.  
  
   - `defaultIcon`: Ein Symbol, das für diesen Dateityp verwendet werden soll. Das Symbol muss als Datei Ressource im Anwendungs Manifest hinzugefügt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Einschließen einer Datendatei in eine ClickOnce-Anwendung](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Ein Beispiel für das `file` -Element und das `fileAssociation` - [ \<fileAssociation> Element](../deployment/fileassociation-element-clickonce-application.md)finden Sie unter Element.  
  
5. Wenn Sie der Anwendung mehr als einen Dateityp zuordnen möchten, fügen Sie weitere `fileAssociation` Elemente hinzu. Beachten Sie, dass das `progid` Attribut für jedes-Attribut unterschiedlich sein sollte.  
  
6. Wenn Sie mit dem Anwendungs Manifest fertig sind, Signieren Sie das Manifest erneut. Dies können Sie über die Befehlszeile über Mage.exe tun.  
  
    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
    Weitere Informationen finden Sie unter [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) .  
  
## <a name="see-also"></a>Weitere Informationen  
 [\<fileAssociation> Gewisses](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (Tool zum Generieren und Bearbeiten von Manifesten)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
