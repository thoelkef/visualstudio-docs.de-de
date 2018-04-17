---
title: 'Vorgehensweise: angeben ein Namens im Startmenü, für eine ClickOnce-Anwendung | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: a27adbd81db29b413bf85b2c7a465897eaeac987
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Gewusst wie: Angeben eines Namens im Startmenü für eine ClickOnce-Anwendung
Wenn eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung für die Verwendung von Online- und Offlineanalyse installiert ist, ein Eintrag hinzugefügt wird die **starten** im Menü und die **Software** Liste. Wird standardmäßig der angezeigte Name ist der Name der Anwendungsassembly identisch, aber Sie können den Anzeigenamen ändern, indem Sie festlegen **Produktname** in der **Veröffentlichungsoptionen** (Dialogfeld).  
  
 **Produktname** wird angezeigt, auf der Seite "publish.htm"; für eine installierte offline-Anwendung werden der Name des Eintrags im der **starten** Menü, und es werden auch der Name, der im zeigt **hinzufügen oder entfernen Programme**.  
  
 **Herausgebername** erscheint auf der Seite "publish.htm" oben **Produktname**, und für eine installierte offline-Anwendung, es ist auch der Name des Ordners, der in der Anwendung enthält die **starten**  Menü.  
  
 Können Sie festlegen, die **Produktname** und **Herausgebername** Eigenschaften in der **Veröffentlichungsoptionen** (Dialogfeld), verfügbar auf der **veröffentlichen** Seite von der **Projekt-Designer**.  
  
### <a name="to-specify-a-start-menu-name"></a>Angeben ein Namens im Startmenü  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Optionen** die Schaltfläche, um die **Veröffentlichungsoptionen** (Dialogfeld).  
  
4.  Klicken Sie auf **Beschreibung**.  
  
5.  In der **Veröffentlichungsoptionen** Dialogfeld Geben Sie den Namen der anzuzeigenden **Produktname**.  
  
6.  Optional können Sie einen Herausgebernamen in eingeben **Herausgebername**.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)