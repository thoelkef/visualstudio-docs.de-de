---
title: Seite "Sicherheit", Projekt-Designer
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29723f5e253a2ff6d4f6c35e8ad8d3e09e2393f1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748657"
---
# <a name="security-page-project-designer"></a>Seite "Sicherheit", Projekt-Designer

Die Seite **Sicherheit** im **Projekt-Designer** wird verwendet, um Einstellungen für die Codezugriffssicherheit von Anwendungen zu konfigurieren, die mit ClickOnce bereitgestellt werden. Weitere Informationen finden Sie unter [Code Access Security for ClickOnce Applications (Codezugriffssicherheit für ClickOnce-Anwendungen)](../../deployment/code-access-security-for-clickonce-applications.md).

Klicken Sie zum Aufrufen der Seite **Sicherheit** zunächst im **Projektmappen-Explorer** auf einen Projektknoten und anschließend im Menü **Projekt** auf **Eigenschaften**. Sobald der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Sicherheit**.

## <a name="security-settings"></a>Sicherheitseinstellungen

 **ClickOnce-Sicherheitseinstellungen aktivieren**

Bestimmt, ob die Sicherheitseinstellungen schon zur Entwurfszeit aktiviert sind Sobald diese Option deaktiviert wird, sind alle anderen Optionen auf der Seite **Sicherheit** nicht mehr verfügbar.

> [!NOTE]
> Wenn Sie eine Anwendung über den **Veröffentlichungs**-Assistenten veröffentlichen, wird diese Option automatisch aktiviert.

Wenn Sie diese Option auswählen, müssen Sie sich zwischen zwei Optionsfeldern entscheiden: **Dies ist eine voll vertrauenswürdige Anwendung** oder **Dies ist eine teilweise vertrauenswürdige Anwendung**.

Diese Option ist für WPF-Webbrowser-Anwendungsprojekte standardmäßig aktiviert.

Für alle anderen Projekttypen ist diese Option standardmäßig deaktiviert.

 **Voll vertrauenswürdige Anwendung**

Wenn Sie diese Option auswählen, fordert die Anwendung „Voll vertrauenswürdig“-Berechtigungen an, wenn sie auf einem Clientcomputer installiert oder ausgeführt wird. Vermeiden Sie „Voll vertrauenswürdig“-Berechtigungen wenn möglich, da der Anwendung uneingeschränkter Zugriff auf Ressourcen wie das Dateisystem und die Registrierung gewährt wird.

Diese Option ist für WPF-Webbrowser-Anwendungsprojekte standardmäßig auf „Teilweise vertrauenswürdig“ festgelegt.

Für alle anderen Projekttypen ist diese Option standardmäßig auf „Voll vertrauenswürdig“ festgelegt.

 **Teilweise vertrauenswürdige Anwendung**

Wenn Sie diese Option auswählen, fordert die Anwendung „Teilweise vertrauenswürdig“-Berechtigungen an, wenn sie auf einem Clientcomputer installiert oder ausgeführt wird. *Teilweise vertrauenswürdig* bedeutet, dass nur die Aktionen, die unter den angeforderten Codezugriffssicherheitsberechtigungen ausgeführt werden, zugelassen werden. Weitere Informationen zur Konfiguration der Sicherheitsberechtigung finden Sie unter [Code Access Security for ClickOnce Applications (Codezugriffssicherheit für ClickOnce-Anwendungen)](../../deployment/code-access-security-for-clickonce-applications.md).

Sie können die „Teilweise vertrauenswürdig“-Sicherheitseinstellungen angeben, indem Sie die Optionen im Bereich **ClickOnce-Sicherheitsberechtigungen** konfigurieren.

## <a name="clickonce-security-permissions"></a>ClickOnce-Sicherheitsberechtigungen

 **Zone, aus der die Anwendung installiert wird**

Gibt verschiedene Standardsicherheitsberechtigungen für den Codezugriff an. Klicken Sie auf **Internet** oder **Lokales Intranet** für eingeschränkte Berechtigungen oder auf **(Benutzerdefiniert)** , um benutzerdefinierte Berechtigungen zu konfigurieren. Wenn die Anwendung mehr Berechtigungen anfordert als ihr in einer Zone gewährt werden, erscheint eine ClickOnce-Vertrauensaufforderung, damit der Benutzer zusätzliche Berechtigungen erteilen kann. Weitere Informationen zur Konfiguration der Sicherheitsberechtigung finden Sie unter [Code Access Security for ClickOnce Applications (Codezugriffssicherheit für ClickOnce-Anwendungen)](../../deployment/code-access-security-for-clickonce-applications.md).

Diese Option ist für WPF-Webbrowser-Anwendungsprojekte standardmäßig auf **Internet** festgelegt.

 **XML-Berechtigungen bearbeiten**

Öffnet die Anwendungsmanifestvorlage („app.manifest“) zur Konfiguration der **(benutzerdefinierten)** Berechtigungen.

 **Erweitert**

Öffnet das [Dialogfeld „Erweiterte Sicherheitseinstellungen“](../../ide/reference/advanced-security-settings-dialog-box.md), das verwendet wird, um Einstellungen zum Debuggen der Anwendung mit eingeschränkten Berechtigungen zu konfigurieren. Diese Einstellungen werden beim Debuggen überprüft, und Berechtigungsausnahmen deuten darauf hin, dass die Anwendung mehr Berechtigungen als in der Zone definiert benötigen.

## <a name="see-also"></a>Siehe auch

- <xref:System.Security.Permissions.WebBrowserPermission>
- <xref:System.Security.Permissions.MediaPermission>
- [Codezugriffssicherheit für ClickOnce-Anwendungen](../../deployment/code-access-security-for-clickonce-applications.md)
- [Vorgehensweise: Aktivieren von ClickOnce-Sicherheitseinstellungen](../../deployment/how-to-enable-clickonce-security-settings.md)
- [Vorgehensweise: Festlegen einer Sicherheitszone für eine ClickOnce-Anwendung](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Vorgehensweise: Festlegen benutzerdefinierter Berechtigungen für eine ClickOnce-Anwendung](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Vorgehensweise: Debuggen einer ClickOnce-Anwendung mit eingeschränkten Berechtigungen](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [ClickOnce-Sicherheit und Bereitstellung](../../deployment/clickonce-security-and-deployment.md)
- [Projekteigenschaftenverweise](../../ide/reference/project-properties-reference.md)
- [Dialogfeld „Erweiterte Sicherheitseinstellungen“](../../ide/reference/advanced-security-settings-dialog-box.md)