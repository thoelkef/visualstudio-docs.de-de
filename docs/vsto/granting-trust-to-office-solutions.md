---
title: Vertrauen zu Office-Lösungen gewähren
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf7a68d5d3567305e4f70049d76a1c260ddecf25
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301656"
---
# <a name="grant-trust-to-office-solutions"></a>Vertrauen zu Office-Lösungen gewähren
  Vertrauen zu Office-Lösungen zu gewähren bedeutet, dass die Sicherheitsrichtlinie jedes Zielcomputers geändert wird, um der Lösungsassembly, dem Anwendungsmanifest, dem Bereitstellungsmanifest und dem Dokument zu vertrauen. Der Office-Lösung kann entweder von Ihnen oder dem Endbenutzer vertrauenswürdiger Vertrauter gewährt werden.

 Sie können der Office-Lösung volle Vertrauenswürdigkeit gewähren, indem Sie die Anwendungs- und Bereitstellungsmanifeste signieren.

 Endbenutzer können der Office-Lösung Vertrauen gewähren, [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] indem sie eine Vertrauensentscheidung in der Vertrauensaufforderung treffen.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a>Vertrauen Sie der Lösung, indem Sie die Anwendungs- und Bereitstellungsmanifeste signieren
 Alle Anwendungs- und Bereitstellungsmanifeste für Office-Lösungen müssen mit einem Zertifikat signiert werden, das den Herausgeber identifiziert. Zertifikate bilden die Grundlage für Vertrauensentscheidungen.

 Ein temporäres Zertifikat wird für Sie erstellt und zur Buildzeit vertrauenswürdig gewährt, sodass die Lösung ausgeführt wird, während Sie sie debuggen. Wenn Sie eine Lösung veröffentlichen, die mit einem temporären Zertifikat signiert ist, wird der Endbenutzer aufgefordert, eine Vertrauensentscheidung zu treffen.

 Wenn Sie die Lösung mit einem bekannten und vertrauenswürdigen Zertifikat signieren, wird die Lösung automatisch installiert, ohne den Endbenutzer aufzufordert, eine Vertrauensentscheidung zu treffen. Weitere Informationen zum Abrufen eines Zertifikats zum Signieren finden Sie unter [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md). Nachdem ein Zertifikat abgerufen wurde, muss das Zertifikat explizit vertrauenswürdig sein, indem es der Liste der vertrauenswürdigen Verleger hinzugefügt wird. Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen eines vertrauenswürdigen Herausgebers zu einem Clientcomputer für ClickOnce-Anwendungen](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Wenn ein Entwickler die Lösung mit einem temporären Zertifikat signiert, kann ein Administrator die Anpassung mit einem bekannten und vertrauenswürdigen Zertifikat erneut signieren, indem er das Manifestgenerierungs- und Bearbeitungstool (*mage.exe*), eines der Microsoft .NET Framework-Tools, verwendet. Weitere Informationen zum Signieren von Lösungen finden Sie unter [Gewusst wie: Signieren von Office-Lösungen](../vsto/how-to-sign-office-solutions.md) und [Anleitungen: Signieren von Anwendungs- und Bereitstellungsmanifesten](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>Vertrauen Sie der Lösung, indem Sie die ClickOnce-Vertrauensaufforderung verwenden
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]fordert den Endbenutzer auf, die Vertrauensentscheidung zu treffen, wenn keine organisationsweite Richtlinie vorhanden ist, die dem Zertifikat der Lösung vertraut. Wenn der Endbenutzer der Lösung Vertrauen gewährt, wird ein Eintrag in der Einschlussliste erstellt, der eine URL und einen öffentlichen Schlüssel zum Speichern dieser Vertrauensentscheidung enthält. Wenn eine vertrauenswürdige Anpassung später ausgeführt wird, wird der Endbenutzer nicht erneut aufgefordert.

 Administratoren können [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] die Vertrauensaufforderung deaktivieren oder verlangen, dass die Eingabeaufforderung nur für Lösungen erfolgt, die mit einem Authenticode-Zertifikat signiert sind. Weitere Informationen zum Ändern dieser Einstellungen für die Zonen MyComputer, LocalIntranet, Internet, TrustedSites und UntrustedSites finden Sie unter [Gewusst wie: Konfigurieren des Vertrauensaufforderungsverhaltens von ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>Weitere Informationen

- [Sichere Office-Lösungen](../vsto/securing-office-solutions.md)
- [Vertrauensstellung zu Dokumenten](../vsto/granting-trust-to-documents.md)
- [Fehlerbehebung bei der Sicherheit von Office-Lösungen](../vsto/troubleshooting-office-solution-security.md)
- [Spezifische Sicherheitsüberlegungen für Office-Lösungen](../vsto/specific-security-considerations-for-office-solutions.md)