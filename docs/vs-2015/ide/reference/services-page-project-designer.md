---
title: Services-Seite, Projekt-Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
ms.assetid: 6dd9e0fa-acba-4d7d-b081-705b0fc86ff5
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 11e1cd997c76974e7b4b8771c0579c175469eca6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665478"
---
# <a name="services-page-project-designer"></a>Services-Seite, Projekt-Designer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Clientanwendungsdienste ermöglichen vereinfachten Zugriff auf [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)]-Anmeldung, Rollen und Profildienste von Windows Forms- und Windows Presentation Foundation-Anwendungen (WPF). Sie können die Clientanwendungsdienste auf der Seite **Dienste** im **Projekt-Designer** aktivieren und konfigurieren.

 Mit den Clientanwendungsdiensten können Sie einen zentralisierten Server verwenden, um Benutzer zu authentifizieren, deren Rolle oder Rollen festzustellen und die Anwendungseinstellungen jedes einzelnen Benutzers, die Sie im Netzwerk freigeben können, zu speichern. Weitere Informationen finden Sie unter [Clientanwendungsdienste](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e).

 Wählen Sie zum Aufrufen der Seite **Dienste** im **Projektmappenexplorer**einen Projektknoten aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**. Sobald der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Dienste**.

> [!NOTE]
> Clientanwendungsdienste erfordern die Vollversion von .NET Framework und werden im .NET Framework Client Profile nicht unterstützt. Wenn das Kontrollkästchen **Clientanwendungsdienste aktivieren** deaktiviert ist, stellen Sie sicher, dass als **Zielframework** das .NET Framework 3.5 oder höher festgelegt ist. Um die Einstellung **Zielframework** in C# anzuzeigen, öffnen Sie den Projekt-Designer, und klicken Sie dann auf die Seite **Anwendung**. Um die Einstellung **Zielframework** in Visual Basic anzuzeigen, öffnen Sie den Projekt-Designer, klicken Sie auf die Seite **Kompilieren** und dann auf **Erweiterte Kompilierungsoptionen**.

## <a name="task-list"></a>Aufgabenliste
 [Gewusst wie: Konfigurieren von Clientanwendungsdiensten](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)

## <a name="uielement-list"></a>UIElement-Liste
 **Konfiguration** Dieses Steuerelement kann auf dieser Seite nicht bearbeitet werden. Eine Beschreibung dieses Steuerelements finden Sie unter [Seite „Kompilieren“, Projekt-Designer (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) oder unter [Seite „Erstellen“, Projekt-Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Plattform:** Dieses Steuerelement kann auf dieser Seite nicht bearbeitet werden. Eine Beschreibung dieses Steuerelements finden Sie unter [Seite „Kompilieren“, Projekt-Designer (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) oder unter [Seite „Erstellen“, Projekt-Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Client Anwendungsdienste aktivieren** Aktivieren Sie diese Option, um Client Anwendungsdienste zu aktivieren. Sie müssen auf der Seite **Dienste** die Speicherorte der Dienste angeben, um Clientanwendungsdienste verwenden zu können.

 **Windows-Authentifizierung verwenden** Gibt an, dass der Authentifizierungs Anbieter die Windows-basierte Authentifizierung verwendet, d. h. die vom Windows-Betriebssystem bereitgestellte Identität.

 **Verwenden der Formular Authentifizierung** Gibt an, dass der Authentifizierungs Anbieter die Formular Authentifizierung verwendet. Das bedeutet, dass Ihre Anwendung eine Benutzeroberfläche für die Anmeldung haben muss. Weitere Informationen finden Sie unter [Vorgehensweise: Implementieren einer Benutzeranmeldung mit Clientanwendungsdiensten](https://msdn.microsoft.com/library/5431a671-eb02-4e18-a651-24764fccec9a).

 **Speicherort für Authentifizierungsdienst** Wird nur mit der Formular Authentifizierung verwendet. Gibt den Speicherort des Authentifizierungsdienst an.

 **Optional: Anmelde Informationsanbieter** Wird nur mit der Formular Authentifizierung verwendet. Gibt die <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>-Implementierung an, die der Authentifizierungsdienst verwendet, um ein Anmeldungsdialogfeld anzuzeigen, wenn Ihre Anwendung die `static`<xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>-Methode aufruft und leere Zeichenfolgen übergibt oder `null` für die Parameter. Wenn Sie dieses Feld leer lassen, müssen Sie einen gültigen Benutzernamen und ein gütiges Kennwort an die <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>-Methode übergeben. Sie müssen einen Anmeldeinformationsanbieter als einen von der Assembly qualifizierten Typnamen angeben. Weitere Informationen finden Sie unter <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> und [Assemblynamen](https://msdn.microsoft.com/library/8f8c2c90-f15d-400e-87e7-a757e4f04d0e). In seiner einfachsten Form sieht ein von der Assembly qualifizierter Typname wie im folgenden Beispiel aus: `MyNamespace.MyLoginClass, MyAssembly`

 **Speicherort für Rollen Dienst** Gibt den Speicherort des Rollen Dienes an.

 **Speicherort des webeinstellungs Diensts** Gibt den Speicherort des Profil Diensts (webeinstellungs Dienst) an.

 **Erweitert** Öffnet das [Dialog Feld Erweiterte Einstellungen für Dienste](../../ide/reference/advanced-settings-for-services-dialog-box.md), das Sie verwenden können, um das Standardverhalten zu überschreiben. Sie können dieses Dialogfeld beispielsweise dafür verwenden, eine Datenbank für Offlinespeicher festzulegen, statt dafür das lokale Dateisystem zu benutzen. Weitere Informationen zu diesem Dialogfeld finden Sie unter [Dialogfeld „Erweiterte Einstellungen für Dienste“](../../ide/reference/advanced-settings-for-services-dialog-box.md).

## <a name="see-also"></a>Weitere Informationen
 Dialog Feld " [Client Anwendungsdienste](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e) [Erweiterte Einstellungen für Dienste](../../ide/reference/advanced-settings-for-services-dialog-box.md) " Gewusst [wie: Konfigurieren von Client Anwendungsdienste](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8) [Seite "kompilieren", Projekt-Designer (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) [Seite "erstellen", Projekt-Designer (c#)](../../ide/reference/build-page-project-designer-csharp.md) [Einführung in den Projekt-Designer](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7)
