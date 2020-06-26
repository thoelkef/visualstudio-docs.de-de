---
title: Ändern der Veröffentlichungs Sprache für die ClickOnce-Anwendung
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0252cf39f8f5ee268adbf625f03a9b5a305b903a
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382587"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Vorgehensweise: Ändern der Sprache für die Veröffentlichung einer ClickOnce-Anwendung

Beim Veröffentlichen einer- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung wird die Benutzeroberfläche, die während der Installation angezeigt wird, standardmäßig auf die Sprache und Kultur Ihres Entwicklungs Computers angewendet. Wenn Sie eine lokalisierte Anwendung veröffentlichen, müssen Sie eine Sprache und eine Kultur angeben, die mit der lokalisierten Version verglichen werden soll. Dies wird durch die- `Publish language` Eigenschaft für Ihr Projekt festgelegt.

Die- `Publish language` Eigenschaft kann im Dialogfeld **Veröffentlichungs Optionen** festgelegt werden, das über die Seite **veröffentlichen** des **Projekt-Designers**zugänglich ist.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

## <a name="to-change-the-publish-language"></a>So ändern Sie die Veröffentlichungs Sprache

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Klicken Sie auf die Schaltfläche **Optionen** , um das Dialogfeld **Veröffentlichungs Optionen** zu öffnen.

4. Klicken Sie auf **Beschreibung**.

5. Wählen Sie im Dialogfeld **Veröffentlichungs Optionen** in der Dropdown Liste **Veröffentlichungs Sprache** eine Sprache und Kultur aus, und klicken Sie dann auf **OK**.

## <a name="see-also"></a>Siehe auch

- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [How to: Publish a ClickOnce application using the Publish Wizard (Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Veröffentlichungs-Assistenten)](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)