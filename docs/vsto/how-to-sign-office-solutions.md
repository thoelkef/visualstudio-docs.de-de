---
title: 'Vorgehensweise: Signieren von Office-Projektmappen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1fff7555c17f4fdac43de2690f8e133cc32881db
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62971120"
---
# <a name="how-to-sign-office-solutions"></a>Vorgehensweise: Signieren von Office-Projektmappen
  Wenn Sie eine Lösung angemeldet haben, können Sie vertrauen für die Projektmappe, die mithilfe des Zertifikats als Beweis gewähren. Sie können das gleiche Zertifikat für mehrere Lösungen verwenden, und alle Lösungen werden mit keine Erhöhung der Sicherheit richtlinienupdates vertrauenswürdig sein.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Wenn Sie die Anwendung manuell bearbeiten und die Bereitstellungsmanifeste mit dem Manifest Generation and Editing Tool (*mage.exe* und *mageui.exe*), müssen Sie die Manifeste neu signieren, bevor Sie sie verwenden können. Weitere Informationen finden Sie unter [Vorgehensweise: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifesten](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="sign-by-using-a-certificate"></a>Melden Sie sich mit einem Zertifikat
 Ein Zertifikat ist eine Datei, die einen eindeutigen Schlüssel und die Identität des Lösungsherausgebers enthält. Sie können Zertifikate von einer Zertifizierungsstelle erwerben oder erstellen Ihr eigenes Zertifikat und eine Zertifizierungsstelle signieren.

 Visual Studio meldet sich an Office-Projektmappen mit einem temporären Zertifikat aus, um Debuggen zu aktivieren. Sie sollten das temporäre Zertifikat nicht als Beweis in bereitgestellten Projektmappen verwenden.

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Eine Office-Projektmappe mit einem Zertifikat signieren

1. Auf der **Projekt** Menü klicken Sie auf _SolutionName_**Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Signierung**.

3. Wählen Sie **ClickOnce-Manifeste signieren**.

4. Suchen Sie das Zertifikat, indem Sie auf **wählen Sie aus dem Store** oder **aus Datei wählen** , und navigieren Sie zu dem Zertifikat.

5. Um sicherzustellen, dass das richtige Zertifikat verwendet wird, klicken Sie auf **Weitere Details** die Zertifikatinformationen an.

## <a name="see-also"></a>Siehe auch

- [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)
- [Gewähren von Vertrauen für Office-Projektmappen](../vsto/granting-trust-to-office-solutions.md)
- [Seite „Signierung“, Projekt-Designer](../ide/reference/signing-page-project-designer.md)
