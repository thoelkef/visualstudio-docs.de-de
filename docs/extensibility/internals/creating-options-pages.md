---
title: Erstellen von Optionsseiten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 368efaa78a56723d4a72c482bea9ee739385127e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709152"
---
# <a name="create-options-pages"></a>Erstellen von Optionsseiten
Im [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Verwalteten Paketframework erweitern <xref:Microsoft.VisualStudio.Shell.DialogPage> Klassen, die von der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE abgeleitet werden, indem sie **Optionsseiten** im Menü **Extras** hinzufügen.

 Ein Objekt, das eine bestimmte **Tools-Option-Seite** implementiert, wird bestimmten VSPackages vom <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Objekt zugeordnet.

 Da die Umgebung das Objekt instanziiert, das eine bestimmte **Tools-Optionsseite** implementiert, wenn diese bestimmte Seite von der IDE angezeigt wird:

- Eine **Seite "Tools-Option"** sollte für ihr eigenes Objekt implementiert werden und nicht für das Objekt, das ein VSPackage implementiert.

- Ein Objekt kann nicht mehrere **Tools-Optionsseiten** implementieren.

## <a name="register-as-a-tools-options-page-provider"></a>Registrieren als Tools Options Seitenanbieter
 Ein VSPackage, das die Benutzerkonfiguration über **die Tools-Optionen-Seiten** unterstützt, <xref:Microsoft.VisualStudio.Shell.Package> gibt die Objekte an, die diese **Tools-Optionsseiten** bereitstellen, indem Instanzen angewendet <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> werden, die auf die Implementierung angewendet werden.

 Es muss eine <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Instanz <xref:Microsoft.VisualStudio.Shell.DialogPage>für jeden -abgeleiteten Typ vorhanden sein, der eine Seite **"Tools-Optionen"** implementiert.

 Jede Instanz <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> verwendet den Typ, der die Seite **Tools-Optionen** implementiert, Zeichenfolgen, die die Kategorie und Unterkategorie enthalten, die zum Identifizieren einer Seite **"Tools-Optionen"** verwendet wird, und Ressourceninformationen zum Registrieren des Typs als Bereitstellung einer Seite **"Tools-Optionen".**

## <a name="persist-tools-options-page-state"></a>Seitenstatus "Persist Tools Options"
 Wenn eine Seitenimplementierung für **Tools-Optionen** registriert ist, ist die Automatisierungsunterstützung aktiviert, die IDE behält den Status der Seite zusammen mit allen anderen Seiten **der Tools-Optionen** bei.

 Ein VSPackage kann seine eigene <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>Persistenz mithilfe von verwalten. Es sollte nur die eine oder andere Methode der Persistenz verwendet werden.

## <a name="implement-dialogpage-class"></a>Implementieren der DialogPage-Klasse
 Ein Objekt, das die Implementierung <xref:Microsoft.VisualStudio.Shell.DialogPage>eines -derived-Typs durch ein VSPackage bereitstellt, kann die folgenden geerbten Features nutzen:

- Ein Standardfenster für die Benutzeroberfläche.

- Ein standardmäßiger Persistenzmechanismus, der entweder verfügbar ist, wenn <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> er auf die Klasse angewendet wird, oder wenn <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> die Eigenschaft `true` auf die festgelegt ist, die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> auf die Klasse angewendet wird.

- Automatisierungsunterstützung.

  Die Mindestanforderung für ein Objekt, <xref:Microsoft.VisualStudio.Shell.DialogPage> das eine Seite **"Tools-Optionen"** implementiert, ist das Hinzufügen öffentlicher Eigenschaften.

  Wenn die Klasse ordnungsgemäß als Seitenanbieter **für Tools-Optionen** registriert ist, sind ihre öffentlichen Eigenschaften im Abschnitt **Optionen** des Menüs **Extras** in Form eines Eigenschaftenrasters verfügbar.

  Alle diese Standardfunktionen können überschrieben werden. Um beispielsweise eine komplexere Benutzeroberfläche zu erstellen, muss <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>nur die Standardimplementierung von überschreiben.

## <a name="example"></a>Beispiel
 Was folgt, ist eine einfache "Hallo Welt" Implementierung einer Optionsseite. Wenn Sie den folgenden Code zu einem Standardprojekt hinzufügen, das von der Visual Studio-Paketvorlage mit der ausgewählten **Menübefehlsoption** erstellt wurde, wird die Funktionsfunktionalität der Optionsseiten angemessen veranschaulicht.

### <a name="description"></a>BESCHREIBUNG
 Die folgende Klasse definiert eine minimale Seite mit den Optionen "Hello World". Beim Öffnen kann der Benutzer `HelloWorld` die öffentliche Eigenschaft in einem Eigenschaftenraster festlegen.

### <a name="code"></a>Code
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]

### <a name="description"></a>BESCHREIBUNG
 Wenn Sie das folgende Attribut auf die Paketklasse anwenden, wird die Optionsseite beim Laden des Pakets verfügbar. Bei den Zahlen handelt es sich um beliebige Ressourcen-IDs für die Kategorie und die Seite, und der boolesche Wert am Ende gibt an, ob die Seite die Automatisierung unterstützt.

### <a name="code"></a>Code
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]

### <a name="description"></a>BESCHREIBUNG
 Der folgende Ereignishandler zeigt ein Ergebnis in Abhängigkeit vom Wert der Eigenschaft an, die auf der Optionsseite festgelegt ist. Es verwendet <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> die Methode, wobei das Ergebnis explizit in den benutzerdefinierten Optionsseitentyp umgewandelt wird, um auf die Eigenschaften zuzugreifen, die von der Seite verfügbar gemacht werden.

 Rufen Sie im Fall eines von der Paketvorlage `MenuItemCallback` generierten Projekts diese Funktion aus der Funktion auf, um sie an den Standardbefehl anzuhängen, der dem Menü **Extras** hinzugefügt wird.

### <a name="code"></a>Code
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von Benutzereinstellungen und -optionen](../../extensibility/extending-user-settings-and-options.md)
- [Automatisierungsunterstützung für Optionsseiten](../../extensibility/internals/automation-support-for-options-pages.md)
