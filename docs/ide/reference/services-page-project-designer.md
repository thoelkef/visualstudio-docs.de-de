---
title: Services-Seite, Projekt-Designer | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
ms.assetid: 6dd9e0fa-acba-4d7d-b081-705b0fc86ff5
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3a44dc8304274bf0633e891690f6b34d2637dfa1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="services-page-project-designer"></a>Services-Seite, Projekt-Designer
Clientanwendungsdienste ermöglichen vereinfachten Zugriff auf [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)]-Anmeldung, Rollen und Profildienste von Windows Forms- und Windows Presentation Foundation-Anwendungen (WPF). Sie können die Clientanwendungsdienste auf der Seite **Dienste** im **Projekt-Designer** aktivieren und konfigurieren.  
  
 Mit den Clientanwendungsdiensten können Sie einen zentralisierten Server verwenden, um Benutzer zu authentifizieren, deren Rolle oder Rollen festzustellen und die Anwendungseinstellungen jedes einzelnen Benutzers, die Sie im Netzwerk freigeben können, zu speichern. Weitere Informationen finden Sie unter [Clientanwendungsdienste](/dotnet/framework/common-client-technologies/client-application-services).  
  
 Wählen Sie zum Aufrufen der Seite **Dienste** im **Projektmappenexplorer**einen Projektknoten aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**. Sobald der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Dienste**.  
  
> [!NOTE]
>  Clientanwendungsdienste erfordern die Vollversion von .NET Framework und werden im .NET Framework Client Profile nicht unterstützt. Wenn das Kontrollkästchen **Clientanwendungsdienste aktivieren** deaktiviert ist, stellen Sie sicher, dass als **Zielframework** das .NET Framework 3.5 oder höher festgelegt ist. Um die Einstellung **Zielframework** in C# anzuzeigen, öffnen Sie den Projekt-Designer, und klicken Sie dann auf die Seite **Anwendung**. Um die Einstellung **Zielframework** in Visual Basic anzuzeigen, öffnen Sie den Projekt-Designer, klicken Sie auf die Seite **Kompilieren** und dann auf **Erweiterte Kompilierungsoptionen**.  
  
## <a name="task-list"></a>Aufgabenliste  
 [Vorgehensweise: Konfigurieren von Clientanwendungsdiensten](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Konfiguration**  
 Dieses Steuerelement kann auf dieser Seite nicht bearbeitet werden. Eine Beschreibung dieses Steuerelements finden Sie unter [Seite „Kompilieren“, Projekt-Designer (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) oder unter [Seite „Erstellen“, Projekt-Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Plattform**  
 Dieses Steuerelement kann auf dieser Seite nicht bearbeitet werden. Eine Beschreibung dieses Steuerelements finden Sie unter [Seite „Kompilieren“, Projekt-Designer (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) oder unter [Seite „Erstellen“, Projekt-Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Clientanwendungsdienste aktivieren**  
 Auswählen, um Clientanwendungsdienste zu aktivieren. Sie müssen auf der Seite **Dienste** die Speicherorte der Dienste angeben, um Clientanwendungsdienste verwenden zu können.  
  
 **Verwenden der Windows-Authentifizierung**  
 Gibt an, dass der Authentifizierungsanbieter die Windows basierte Authentifizierung verwendet, sprich die durch das Windows-Betriebssystem angegebene Identität.  
  
 **Verwenden der Formularauthentifizierung**  
 Gibt an, dass der Authentifizierungsanbieter Formularauthentifizierung verwendet. Das bedeutet, dass Ihre Anwendung eine Benutzeroberfläche für die Anmeldung haben muss. Weitere Informationen finden Sie unter [Vorgehensweise: Implementieren einer Benutzeranmeldung mit Clientanwendungsdiensten](/dotnet/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services).  
  
 **Speicherort des Authentifizierungsdiensts**  
 Wird nur bei der Formularauthentifizierung verwendet. Gibt den Speicherort des Authentifizierungsdienst an.  
  
 **Optional: Anbieter von Anmeldeinformationen**  
 Wird nur bei der Formularauthentifizierung verwendet. Gibt die <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>-Implementierung an, die der Authentifizierungsdienst verwendet, um ein Anmeldungsdialogfeld anzuzeigen, wenn Ihre Anwendung die `static`<xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>-Methode aufruft und leere Zeichenfolgen übergibt oder `null` für die Parameter. Wenn Sie dieses Feld leer lassen, müssen Sie einen gültigen Benutzernamen und ein gütiges Kennwort an die <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>-Methode übergeben. Sie müssen einen Anmeldeinformationsanbieter als einen von der Assembly qualifizierten Typnamen angeben. Weitere Informationen finden Sie unter <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> und [Assemblynamen](/dotnet/framework/app-domains/assembly-names). In seiner einfachsten Form sieht ein von der Assembly qualifizierter Typname wie im folgenden Beispiel aus: `MyNamespace.MyLoginClass, MyAssembly`  
  
 **Speicherort des Rollendiensts**  
 Gibt den Speicherort des Rollendiensts an.  
  
 **Speicherort des Webeinstellungsdiensts**  
 Gibt den Speicherort des Profildienstes (Webeinstellungen) an.  
  
 **Erweitert**  
 Öffnet das [Dialogfeld „Erweiterte Einstellungen für Dienste“](../../ide/reference/advanced-settings-for-services-dialog-box.md), das Sie verwenden können, um Standardverhalten außer Kraft zu setzen. Sie können dieses Dialogfeld beispielsweise dafür verwenden, eine Datenbank für Offlinespeicher festzulegen, statt dafür das lokale Dateisystem zu benutzen. Weitere Informationen zu diesem Dialogfeld finden Sie unter [Dialogfeld „Erweiterte Einstellungen für Dienste“](../../ide/reference/advanced-settings-for-services-dialog-box.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Clientanwendungsdienste](/dotnet/framework/common-client-technologies/client-application-services)   
 [Dialogfeld „Erweiterte Einstellungen für Dienste“](../../ide/reference/advanced-settings-for-services-dialog-box.md)   
 [Vorgehensweise: Konfigurieren von Clientanwendungsdiensten](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)   
 [Seite „Kompilieren“, Projekt-Designer (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Seite „Erstellen“, Projekt-Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md)   
