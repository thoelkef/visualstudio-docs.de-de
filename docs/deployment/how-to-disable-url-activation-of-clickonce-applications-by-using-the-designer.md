---
title: 'Vorgehensweise: Deaktivieren der URL-Aktivierung von ClickOnce-Anwendungen mithilfe des Designers | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 366c4362ca3c3b6140380ab64000a01fe8e1aa6b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
ms.locfileid: "31558280"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Gewusst wie: Deaktivieren der URL-Aktivierung von ClickOnce-Anwendungen mithilfe des Designers
In der Regel eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung wird automatisch gestartet, sofort nach der Installation von einem Webserver. Aus Gründen der Sicherheit entscheiden, dieses Verhalten deaktivieren, und informieren Benutzer zum Starten der Anwendung aus der **starten** Menü stattdessen. Das folgende Verfahren beschreibt das Deaktivieren der URL-Aktivierung.  
  
 Dieses Verfahren kann nur für [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Anwendungen verwendet werden, die von einem Webserver auf dem Computer des Benutzers installiert werden. Es kann nicht für reine onlineanwendungen, verwendet werden, kann nur mithilfe der URL gestartet werden. Weitere Informationen zu den Unterschieden zwischen reinen onlineanwendungen und installierten Anwendungen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Dieses Verfahren verwendet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sie können diese Aufgabe auch mithilfe der [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Weitere Informationen finden Sie unter [Vorgehensweise: Deaktivieren Sie URL-Aktivierung von ClickOnce-Anwendungen](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Prozedur  
  
#### <a name="to-disable-url-activation-for-your-application"></a>So deaktivieren Sie die URL-Aktivierung für Ihre Anwendung  
  
1.  Mit der rechten Maustaste in des Projektnamen **Projektmappen-Explorer**, und klicken Sie auf **Eigenschaften**.  
  
2.  Auf der **Eigenschaften** auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf **Optionen**.  
  
4.  Klicken Sie auf **Manifeste**.  
  
5.  Aktivieren Sie das Kontrollkästchen mit der Bezeichnung **Anwendung aktiviert wird, über eine URL blockiert**.  
  
6.  Stellen Sie die Anwendung bereit.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)