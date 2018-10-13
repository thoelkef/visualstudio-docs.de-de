---
title: Services-Seite, Projekt-Designer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
ms.assetid: 6dd9e0fa-acba-4d7d-b081-705b0fc86ff5
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3a968283a8836c9a31c1d7f1e6552c8302d87140
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243697"
---
# <a name="services-page-project-designer"></a>Services-Seite, Projekt-Designer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Clientanwendungsdienste ermöglichen vereinfachten Zugriff auf [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)]-Anmeldung, Rollen und Profildienste von Windows Forms- und Windows Presentation Foundation-Anwendungen (WPF). Sie können die Clientanwendungsdienste auf der Seite **Dienste** im **Projekt-Designer** aktivieren und konfigurieren.  
  
 Mit den Clientanwendungsdiensten können Sie einen zentralisierten Server verwenden, um Benutzer zu authentifizieren, deren Rolle oder Rollen festzustellen und die Anwendungseinstellungen jedes einzelnen Benutzers, die Sie im Netzwerk freigeben können, zu speichern. Weitere Informationen finden Sie unter [Clientanwendungsdienste](http://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e).  
  
 Wählen Sie zum Aufrufen der Seite **Dienste** im **Projektmappenexplorer**einen Projektknoten aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**. Sobald der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Dienste**.  
  
> [!NOTE]
>  Clientanwendungsdienste erfordern die Vollversion von .NET Framework und werden im .NET Framework Client Profile nicht unterstützt. Wenn das Kontrollkästchen **Clientanwendungsdienste aktivieren** deaktiviert ist, stellen Sie sicher, dass als **Zielframework** das .NET Framework 3.5 oder höher festgelegt ist. Um die Einstellung **Zielframework** in C# anzuzeigen, öffnen Sie den Projekt-Designer, und klicken Sie dann auf die Seite **Anwendung**. Um die Einstellung **Zielframework** in Visual Basic anzuzeigen, öffnen Sie den Projekt-Designer, klicken Sie auf die Seite **Kompilieren** und dann auf **Erweiterte Kompilierungsoptionen**.  
  
## <a name="task-list"></a>Aufgabenliste  
 [Vorgehensweise: Konfigurieren von Clientanwendungsdiensten](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)  
  
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
 Gibt an, dass der Authentifizierungsanbieter Formularauthentifizierung verwendet. Das bedeutet, dass Ihre Anwendung eine Benutzeroberfläche für die Anmeldung haben muss. Weitere Informationen finden Sie unter [Vorgehensweise: Implementieren einer Benutzeranmeldung mit Clientanwendungsdiensten](http://msdn.microsoft.com/library/5431a671-eb02-4e18-a651-24764fccec9a).  
  
 **Speicherort des Authentifizierungsdiensts**  
 Wird nur bei der Formularauthentifizierung verwendet. Gibt den Speicherort des Authentifizierungsdienst an.  
  
 **Optional: Anbieter von Anmeldeinformationen**  
 Wird nur bei der Formularauthentifizierung verwendet. Gibt die <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>-Implementierung an, die der Authentifizierungsdienst verwendet, um ein Anmeldungsdialogfeld anzuzeigen, wenn Ihre Anwendung die `static`<xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>-Methode aufruft und leere Zeichenfolgen übergibt oder `null` für die Parameter. Wenn Sie dieses Feld leer lassen, müssen Sie einen gültigen Benutzernamen und ein gütiges Kennwort an die <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>-Methode übergeben. Sie müssen einen Anmeldeinformationsanbieter als einen von der Assembly qualifizierten Typnamen angeben. Weitere Informationen finden Sie unter <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> und [Assemblynamen](http://msdn.microsoft.com/library/8f8c2c90-f15d-400e-87e7-a757e4f04d0e). In seiner einfachsten Form sieht ein von der Assembly qualifizierter Typname wie im folgenden Beispiel aus: `MyNamespace.MyLoginClass, MyAssembly`  
  
 **Speicherort des Rollendiensts**  
 Gibt den Speicherort des Rollendiensts an.  
  
 **Speicherort des Webeinstellungsdiensts**  
 Gibt den Speicherort des Profildienstes (Webeinstellungen) an.  
  
 **Erweitert**  
 Öffnet das [Dialogfeld „Erweiterte Einstellungen für Dienste“](../../ide/reference/advanced-settings-for-services-dialog-box.md), das Sie verwenden können, um Standardverhalten außer Kraft zu setzen. Sie können dieses Dialogfeld beispielsweise dafür verwenden, eine Datenbank für Offlinespeicher festzulegen, statt dafür das lokale Dateisystem zu benutzen. Weitere Informationen zu diesem Dialogfeld finden Sie unter [Dialogfeld „Erweiterte Einstellungen für Dienste“](../../ide/reference/advanced-settings-for-services-dialog-box.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Clientanwendungsdienste](http://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e)   
 [Dialogfeld „Erweiterte Einstellungen für Dienste“](../../ide/reference/advanced-settings-for-services-dialog-box.md)   
 [Vorgehensweise: Konfigurieren von Clientanwendungsdiensten](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)   
 [Seite „Kompilieren“, Projekt-Designer (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Seite „Erstellen“, Projekt-Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md)   
 [Introduction to the Project Designer (Einführung in den Projekt-Designer)](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)



