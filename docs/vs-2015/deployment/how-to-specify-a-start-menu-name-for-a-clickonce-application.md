---
title: 'Vorgehensweise: Angeben eines Namens für eine ClickOnce-Anwendung im Menü | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
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
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 98554ef2dc9b1f5bdd3ef1879f32b2c2319a7a1b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49277776"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Gewusst wie: Angeben eines Namens im Startmenü für eine ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung installiert ist, für die online und offline-Verwendung, ein Eintrag hinzugefügt wird die **starten** Menü und die **Programme hinzufügen oder entfernen** Liste. Der Anzeigename wird standardmäßig der Name des der Assembly identisch, aber Sie können den Anzeigenamen ändern, indem Sie die Einstellung **Produktname** in die **Veröffentlichungsoptionen** Dialogfeld.  
  
 **Produktname** erscheint auf der Seite "publish.htm"; für eine offline-Anwendung installiert, werden sie den Namen des Eintrags im der **starten** Menü, und es werden auch der Name, der zeigt, in **hinzufügen oder entfernen Programme**.  
  
 **Name des Herausgebers** erscheint auf der Seite "publish.htm" oben **Produktname**, und für eine installierte Anwendung offline, wird auch der Name des Ordners, der in der Anwendung enthält die **starten**  Menü.  
  
 Sie können festlegen, die **Produktname** und **Herausgebername** Eigenschaften in der **Veröffentlichungsoptionen** im Dialogfeld auf die **veröffentlichen** Seite von der **Projekt-Designer**.  
  
### <a name="to-specify-a-start-menu-name"></a>Angeben ein Namens im Startmenü  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Optionen** die Schaltfläche, um die **Veröffentlichungsoptionen** Dialogfeld.  
  
4.  Klicken Sie auf **Beschreibung**.  
  
5.  In der **Veröffentlichungsoptionen** Dialogfeld Geben Sie den anzuzeigenden Namen **Produktname**.  
  
6.  Optional können Sie einen Herausgebernamen in eingeben **Herausgebername**.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



