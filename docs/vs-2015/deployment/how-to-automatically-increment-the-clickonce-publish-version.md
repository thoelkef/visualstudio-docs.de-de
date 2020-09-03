---
title: 'Gewusst wie: Automatisches Inkrement der ClickOnce-Veröffentlichungs Version | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 50faf70e8eda6ef7ab01201102540729497eb87b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683919"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Gewusst wie: Automatisches Erhöhen der ClickOnce-Veröffentlichungsversion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Veröffentlichen einer- [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung bewirkt das Ändern der- `Publish Version` Eigenschaft, dass die Anwendung als Update veröffentlicht wird. Standardmäßig erhöht Visual Studio automatisch die `Revision` Anzahl von, wenn `Publish Version` Sie die Anwendung veröffentlichen.  
  
 Sie können dieses Verhalten auf der Seite **veröffentlichen** des Projekt- **Designers**deaktivieren.  
  
> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>So deaktivieren Sie die automatische Inkrementierung der Veröffentlichungs Version  
  
1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2. Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3. Deaktivieren Sie im Abschnitt Veröffentlichungs **Version** das Kontrollkästchen **Automatische Schritt weite Revision mit jeder Version** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gewusst wie: Festlegen der ClickOnce-Veröffentlichungs Version](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [How to: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
