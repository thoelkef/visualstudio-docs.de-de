---
title: 'Vorgehensweise: Ändern der Veröffentlichungs Sprache für eine ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26e4074b731dad44cd9eed40f1c1cc755d786562
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683799"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Gewusst wie: Ändern der Veröffentlichungssprache einer ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Veröffentlichen einer- [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung wird die Benutzeroberfläche, die während der Installation angezeigt wird, standardmäßig auf die Sprache und Kultur Ihres Entwicklungs Computers angewendet. Wenn Sie eine lokalisierte Anwendung veröffentlichen, müssen Sie eine Sprache und eine Kultur angeben, die mit der lokalisierten Version verglichen werden soll. Dies wird durch die- `Publish language` Eigenschaft für Ihr Projekt festgelegt.  
  
 Die- `Publish language` Eigenschaft kann im Dialogfeld **Veröffentlichungs Optionen** festgelegt werden, das über die Seite **veröffentlichen** des **Projekt-Designers**zugänglich ist.  
  
> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-change-the-publish-language"></a>So ändern Sie die Veröffentlichungs Sprache  
  
1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2. Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3. Klicken Sie auf die Schaltfläche **Optionen** , um das Dialogfeld **Veröffentlichungs Optionen** zu öffnen.  
  
4. Klicken Sie auf **Beschreibung**.  
  
5. Wählen Sie im Dialogfeld **Veröffentlichungs Optionen** in der Dropdown Liste **Veröffentlichungs Sprache** eine Sprache und Kultur aus, und klicken Sie dann auf **OK**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [How to: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
