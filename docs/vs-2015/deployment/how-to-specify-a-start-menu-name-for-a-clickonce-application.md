---
title: 'Gewusst wie: Angeben eines Startmenü namens für eine ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 30bb4050399bf7a6d9120f7e5454b26ce505af35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149758"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Gewusst wie: Angeben eines Namens im Startmenü für eine ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendung für die Online-und Offline Verwendung installiert wird, wird dem **Startmenü** und der Liste Software **Add or Remove Programs** ein Eintrag hinzugefügt. Standardmäßig ist der Anzeige Name mit dem Namen der Anwendungsassembly identisch, aber Sie können den anzeigen Amen ändern, indem Sie im Dialogfeld **Veröffentlichungs Optionen** den **Product Name** festlegen.  
  
 Der **Produktname** wird auf der Seite "publish.htm" angezeigt. bei einer installierten offline Anwendung handelt es sich um den Namen des Eintrags im **Startmenü** . Außerdem handelt es **sich dabei um**den Namen, der in "Software" angezeigt wird.  
  
 Der **Herausgeber Name** wird auf der publish.htm Seite oberhalb des **Produkt namens**angezeigt, und für eine installierte offline Anwendung ist dies auch der Name des Ordners, der das Anwendungssymbol im **Startmenü** enthält.  
  
 Sie können die Eigenschaften **Produktname** und **Herausgeber Name** im Dialogfeld **Veröffentlichungs Optionen** festlegen, das auf der Seite **veröffentlichen** des **Projekt-Designers**verfügbar ist.  
  
### <a name="to-specify-a-start-menu-name"></a>So geben Sie einen Startmenü Namen an  
  
1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2. Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3. Klicken Sie auf die Schaltfläche **Optionen** , um das Dialogfeld **Veröffentlichungs Optionen** zu öffnen.  
  
4. Klicken Sie auf **Beschreibung**.  
  
5. Geben Sie im Dialogfeld **Veröffentlichungs Optionen** den Namen ein, der unter **Produktname**angezeigt werden soll.  
  
6. Optional können Sie einen Herausgeber Namen in den **Herausgeber Namen**eingeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [How to: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
