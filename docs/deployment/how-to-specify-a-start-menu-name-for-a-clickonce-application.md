---
title: 'Vorgehensweise: Angeben eines Namens für eine ClickOnce-Anwendung im Menü | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6bf265b2e3761ba1fd929e72e29f4c2c47cd449
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079555"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Gewusst wie: Angeben eines Namens für eine ClickOnce-Anwendung im Menü
Wenn eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung installiert ist, für die online und offline-Verwendung, ein Eintrag hinzugefügt wird die **starten** Menü und die **Programme hinzufügen oder entfernen** Liste. Der Anzeigename wird standardmäßig der Name des der Assembly identisch, aber Sie können den Anzeigenamen ändern, indem Sie die Einstellung **Produktname** in die **Veröffentlichungsoptionen** Dialogfeld.  
  
 **Produktname** erscheint auf der *publish.htm* Seite; für eine installierte Anwendung offline, sie den Namen des Eintrags im werden die **starten** Menü, und es werden auch der Name, der zeigt, in **Hinzufügen oder Entfernen von Programmen**.  
  
 **Name des Herausgebers** erscheint auf der *publish.htm* zuvor auf der Seite **Produktname**, und für eine installierte Anwendung offline, wird auch der Name des Ordners, der der Anwendung enthält. Symbol in der **starten** Menü.  
  
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
 [Gewusst wie: veröffentlichen eine ClickOnce-Anwendung, die mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)