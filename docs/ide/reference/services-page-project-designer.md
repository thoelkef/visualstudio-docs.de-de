---
title: "Services-Seite, Projekt-Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesServices"
helpviewer_keywords: 
  - "Seite „Services“ im Projekt-Designer"
  - "Projekt-Designer, Seite „Services“"
ms.assetid: 6dd9e0fa-acba-4d7d-b081-705b0fc86ff5
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Services-Seite, Projekt-Designer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Clientanwendungsdienste ermöglichen den vereinfachten Zugriff auf [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)]\-Anmeldung, \-Rollen und \-Profildienste aus Windows Forms und Windows Presentation Foundation \(WPF\)\-Anwendungen.  Sie können Clientanwendungsdienste für Ihr Projekt auf der Seite **Dienste** des **Projekt\-Designers** aktivieren und konfigurieren.  
  
 Mit Clientanwendungsdiensten können Sie einen zentralen Server zum Authentifizieren von Benutzern verwenden, die den Benutzern zugewiesenen Rollen festlegen und pro Benutzer vorgenommene Anwendungseinstellungen speichern, die Sie im Netzwerk gemeinsam genutzt werden können.  Weitere Informationen finden Sie unter [Clientanwendungsdienste](../Topic/Client%20Application%20Services.md).  
  
 Wenn Sie auf die Seite **Dienste** zugreifen möchten, wählen Sie einen Projektknoten im **Projektmappen\-Explorer** aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**.  Wenn der **Projekt\-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Dienste**.  
  
> [!NOTE]
>  Clientanwendungsdienste benötigen die Vollversion von .NET Framework und werden in .NET Framework Client Profile nicht unterstützt.  Wenn das Kontrollkästchen **Clientanwendungsdienste aktivieren** deaktiviert ist, überprüfen Sie, ob **Zielframework** auf .NET Framework 3.5 oder höher festgelegt ist.  Um die Einstellung **Target framework** in C\# anzuzeigen, öffnen Sie den Projekt\-Designer, und klicken Sie auf die Seite **Anwendung**.  Um die Einstellung **Zielframework** in Visual Basic anzuzeigen, öffnen Sie den Projekt\-Designer, klicken Sie auf die Seite **Kompilieren**, und klicken Sie auf **Erweiterte Kompilierungsoptionen**.  
  
## Aufgabenliste  
 [Gewusst wie: Konfigurieren von Clientanwendungsdiensten](../Topic/How%20to:%20Configure%20Client%20Application%20Services.md)  
  
## UIElement-Liste  
 **Konfiguration**  
 Dieses Steuerelement ist auf dieser Seite nicht bearbeitbar.  Eine Beschreibung dieses Steuerelements finden Sie unter [Seite "Kompilieren", Projekt\-Designer \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md) oder [Seite "Erstellen", Projekt\-Designer \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Plattform**  
 Dieses Steuerelement ist auf dieser Seite nicht bearbeitbar.  Eine Beschreibung dieses Steuerelements finden Sie unter [Seite "Kompilieren", Projekt\-Designer \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md) oder [Seite "Erstellen", Projekt\-Designer \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Clientanwendungsdienste aktivieren**  
 Wählen Sie diese Option, um Clientanwendungsdienste zu aktivieren.  Sie müssen auf der Seite **Dienste** Speicherorte für Dienste angeben, um Clientanwendungsdienste verwenden zu können.  
  
 **Windows\-Authentifizierung verwenden**  
 Gibt an, dass der Authentifizierungsanbieter eine auf Windows basierende Authentifizierung verwendet, d. h. die vom Betriebssystem angegebene Identität.  
  
 **Formularauthentifizierung verwenden**  
 Gibt an, dass der Authentifizierungsanbieter die Formularauthentifizierung verwendet.  Dies bedeutet, dass die Anwendung eine Benutzeroberfläche für die Anmeldung bereitstellen muss.  Weitere Informationen finden Sie unter [Gewusst wie: Implementieren einer Benutzeranmeldung mit Clientanwendungsdiensten](../Topic/How%20to:%20Implement%20User%20Login%20with%20Client%20Application%20Services.md).  
  
 **Speicherort des Authentifizierungsdiensts**  
 Wird nur bei der Formularauthentifizierung verwendet.  Gibt den Speicherort des Authentifizierungsdiensts an.  
  
 **Optional: Anmeldeinformationsanbieter**  
 Wird nur bei der Formularauthentifizierung verwendet.  Gibt die <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>\-Implementierung an, die vom Authentifizierungsdienst zum Anzeigen eines Anmeldedialogfelds verwendet wird, wenn die Anwendung die `static`<xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>\-Methode aufruft und leere Zeichenfolgen oder `null` für die Parameter übergibt.  Wenn Sie dieses Feld leer lassen, müssen Sie einen gültigen Benutzernamen und ein gültiges Kennwort an die <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>\-Methode übergeben.  Sie müssen den Anmeldeinformationsanbieter als einen durch die Assembly qualifizierten Typnamen angeben.  Weitere Informationen finden Sie unter <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> und [Assemblynamen](../Topic/Assembly%20Names.md).  In seiner einfachsten Form sieht ein durch die Assembly qualifizierter Typname wie im folgenden Beispiel aus:`MyNamespace.MyLoginClass, MyAssembly`  
  
 **Speicherort des Rollendiensts**  
 Gibt den Speicherort des Rollendiensts an.  
  
 **Speicherort des Webeinstellungsdiensts**  
 Gibt den Speicherort des Profildiensts \(Webeinstellungsdiensts\) an.  
  
 **Erweitert**  
 Öffnet das [Dialogfeld "Erweiterte Einstellungen für Dienste"](../../ide/reference/advanced-settings-for-services-dialog-box.md), in dem Sie das Standardverhalten überschreiben können.  Sie können mithilfe dieses Dialogfelds beispielsweise eine Datenbank als Offlinespeicher angeben, statt das lokale Dateisystem zu verwenden.  Weitere Informationen finden Sie unter [Dialogfeld "Erweiterte Einstellungen für Dienste"](../../ide/reference/advanced-settings-for-services-dialog-box.md).  
  
## Siehe auch  
 [Clientanwendungsdienste](../Topic/Client%20Application%20Services.md)   
 [Dialogfeld "Erweiterte Einstellungen für Dienste"](../../ide/reference/advanced-settings-for-services-dialog-box.md)   
 [Gewusst wie: Konfigurieren von Clientanwendungsdiensten](../Topic/How%20to:%20Configure%20Client%20Application%20Services.md)   
 [Seite "Kompilieren", Projekt\-Designer \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Seite "Erstellen", Projekt\-Designer \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md)   
 [Introduction to the Project Designer](http://msdn.microsoft.com/de-de/898dd854-c98d-430c-ba1b-a913ce3c73d7)