---
title: Deaktivieren der URL-Aktivierung von ClickOnce-apps mit dem Designer
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 818ab634d48fb666ecab5d89464ea017040bd250
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382483"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Vorgehensweise: Deaktivieren der URL-Aktivierung von ClickOnce-Anwendungen mithilfe des Designers
Eine-Anwendung wird in der Regel [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] automatisch gestartet, sobald Sie von einem Webserver installiert wurde. Aus Sicherheitsgründen können Sie dieses Verhalten deaktivieren und Benutzer dazu auffordern, die Anwendung stattdessen über das **Startmenü** zu starten. Das folgende Verfahren beschreibt das Deaktivieren der URL-Aktivierung.

 Dieses Verfahren kann nur für [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Anwendungen verwendet werden, die von einem Webserver auf dem Computer des Benutzers installiert werden. Sie kann nicht für reine Online Anwendungen verwendet werden, die nur mithilfe Ihrer URL gestartet werden können. Weitere Informationen zum Unterschied zwischen nur Online-und installierten Anwendungen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md).

 Dieses Verfahren verwendet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Sie können diese Aufgabe auch mit dem Ausführen [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Weitere Informationen finden Sie unter Gewusst [wie: Deaktivieren der URL-Aktivierung von ClickOnce-Anwendungen](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).

## <a name="procedure"></a>Verfahren

#### <a name="to-disable-url-activation-for-your-application"></a>So deaktivieren Sie die URL-Aktivierung für Ihre Anwendung

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektnamen, und klicken Sie auf **Eigenschaften**.

2. Klicken Sie auf der Seite **Eigenschaften** auf die Registerkarte **veröffentlichen** .

3. Klicken Sie auf **Optionen**.

4. Klicken Sie auf **Manifests**.

5. Aktivieren Sie das Kontrollkästchen **Anwendung aus Aktivierung über eine URL blockieren**.

6. Stellen Sie Ihre Anwendung bereit.

## <a name="see-also"></a>Siehe auch
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)