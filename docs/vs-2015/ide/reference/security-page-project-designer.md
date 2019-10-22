---
title: Seite „Sicherheit“, Projekt-Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
ms.assetid: 641d9cd3-fa07-498a-8568-3c169bb4d3d5
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 768b0d43d8e6b52781e3f2dc2029e0b96b3a6548
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665535"
---
# <a name="security-page-project-designer"></a>Seite "Sicherheit", Projekt-Designer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Seite **Sicherheit** im **Projekt-Designer** wird verwendet, um Einstellungen für die Codezugriffssicherheit von Anwendungen zu konfigurieren, die mit [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] bereitgestellt werden. Weitere Informationen finden Sie unter [Code Access Security for ClickOnce Applications (Codezugriffssicherheit für ClickOnce-Anwendungen)](../../deployment/code-access-security-for-clickonce-applications.md).

 Klicken Sie zum Aufrufen der Seite **Sicherheit** zunächst im **Projektmappen-Explorer** auf einen Projektknoten und anschließend im Menü **Projekt** auf **Eigenschaften**. Sobald der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Sicherheit**.

## <a name="security-settings"></a>Sicherheitseinstellungen
 **ClickOnce-Sicherheitseinstellungen aktivieren** Bestimmt, ob Sicherheitseinstellungen zur Entwurfszeit aktiviert werden. Sobald diese Option deaktiviert wird, sind alle anderen Optionen auf der Seite **Sicherheit** nicht mehr verfügbar.

> [!NOTE]
> Wenn Sie eine Anwendung über den **Veröffentlichungs**-Assistenten veröffentlichen, wird diese Option automatisch aktiviert.

 Wenn Sie diese Option auswählen, können Sie entscheiden, ob Sie ein oder zwei Optionsfelder aktivieren möchten: **Voll vertrauenswürdige Anwendung** oder **Teilweise vertrauenswürdige Anwendung**.

 Diese Option ist für WPF-Webbrowser-Anwendungsprojekte standardmäßig aktiviert.

 Für alle anderen Projekttypen ist diese Option standardmäßig deaktiviert.

 **Dies ist eine voll vertrauenswürdige Anwendung** . Wenn Sie diese Option auswählen, fordert die Anwendung voll vertrauenswürdige Berechtigungen an, wenn Sie auf einem Client Computer installiert oder ausgeführt wird. Vermeiden Sie „Voll vertrauenswürdig“-Berechtigungen wenn möglich, da der Anwendung uneingeschränkter Zugriff auf Ressourcen wie das Dateisystem und die Registrierung gewährt wird.

 Diese Option ist für WPF-Webbrowser-Anwendungsprojekte standardmäßig auf „Teilweise vertrauenswürdig“ festgelegt.

 Für alle anderen Projekttypen ist diese Option standardmäßig auf „Voll vertrauenswürdig“ festgelegt.

 **Dies ist eine teilweise vertrauenswürdige Anwendung** . Wenn Sie diese Option auswählen, fordert die Anwendung teilweise vertrauenswürdige Berechtigungen an, wenn Sie auf einem Client Computer installiert oder ausgeführt wird. *Teilweise vertrauenswürdig* bedeutet, dass nur die Aktionen, die unter den angeforderten Codezugriffssicherheitsberechtigungen ausgeführt werden, zugelassen werden. Weitere Informationen zur Konfiguration der Sicherheitsberechtigung finden Sie unter [Code Access Security for ClickOnce Applications (Codezugriffssicherheit für ClickOnce-Anwendungen)](../../deployment/code-access-security-for-clickonce-applications.md).

 Sie können die „Teilweise vertrauenswürdig“-Sicherheitseinstellungen angeben, indem Sie die Optionen im Bereich **ClickOnce-Sicherheitsberechtigungen** konfigurieren.

## <a name="clickonce-security-permissions"></a>ClickOnce-Sicherheitsberechtigungen
 **Zone, aus der Ihre Anwendung installiert wird** Gibt einen Standardsatz von Code Zugriffs-Sicherheits Berechtigungen an. Klicken Sie auf **Internet** oder **Lokales Intranet** für eingeschränkte Berechtigungen oder auf **(Benutzerdefiniert)** , um benutzerdefinierte Berechtigungen zu konfigurieren. Wenn die Anwendung mehr Berechtigungen anfordert als ihr in einer Zone gewährt werden, erscheint eine ClickOnce-Vertrauensaufforderung, damit der Benutzer zusätzliche Berechtigungen erteilen kann. Weitere Informationen zur Konfiguration der Sicherheitsberechtigung finden Sie unter [Code Access Security for ClickOnce Applications (Codezugriffssicherheit für ClickOnce-Anwendungen)](../../deployment/code-access-security-for-clickonce-applications.md).

 Diese Option ist für WPF-Webbrowser-Anwendungsprojekte standardmäßig auf **Internet** festgelegt.

 **Berechtigungs-XML bearbeiten** Öffnet die Anwendungs Manifest-Vorlage (app. manifest), um die Berechtigungen für den Berechtigungs Satz **(Benutzer definiert)** zu konfigurieren.

 **Erweitert** Öffnet das [Dialog Feld Erweiterte Sicherheitseinstellungen](../../ide/reference/advanced-security-settings-dialog-box.md), das verwendet wird, um Einstellungen für das Debuggen der Anwendung mit eingeschränkten Berechtigungen zu konfigurieren. Diese Einstellungen werden beim Debuggen überprüft, und Berechtigungsausnahmen deuten darauf hin, dass die Anwendung mehr Berechtigungen als in der Zone definiert benötigen.

## <a name="see-also"></a>Siehe auch
 <xref:System.Security.Permissions.WebBrowserPermission> <xref:System.Security.Permissions.MediaPermission>
 [Code Zugriffssicherheit für ClickOnce-Anwendungen](../../deployment/code-access-security-for-clickonce-applications.md) [Gewusst wie: Aktivieren von ClickOnce-Sicherheitseinstellungen](../../deployment/how-to-enable-clickonce-security-settings.md) Gewusst [wie: Festlegen einer Sicherheits Zone für eine ClickOnce-Anwendung](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md) Gewusst [wie: Festlegen benutzerdefinierter Berechtigungen für eine ClickOnce-Anwendung](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md) Gewusst [wie: Debuggen einer ClickOnce-Anwendung mit eingeschränkten Berechtigungen](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md) [ClickOnce Sicherheit und Bereitstellungs](../../deployment/clickonce-security-and-deployment.md) [Projekteigenschaften Referenz](../../ide/reference/project-properties-reference.md) [Erweiterte Sicherheitseinstellungen (Dialog Feld](../../ide/reference/advanced-security-settings-dialog-box.md) )
