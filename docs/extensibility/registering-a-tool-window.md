---
title: Registrieren eines Tool Fensters | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0387bc15e392d9e9035e4dd1c119fdc1ad00dba
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011969"
---
# <a name="register-a-tool-window"></a>Tool Fenster registrieren
Sie können Ihre Tool Fenster mit <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> und registrieren  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> .

## <a name="example"></a>Beispiel

```csharp

[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]
[ProvideMenuResource(1000, 1)]
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]
public class PackageToolWindow : Package
{
```

 Im obigen Code <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> registriert die `PersistedWindowPane` `DynamicWindowPane` Tool Fenster und bei Visual Studio. Das persistente Tool Fenster wird angedockt und mit **Projektmappen-Explorer**im Registerkarten Format angezeigt, und im dynamischen Fenster wird eine Standard Anfangsposition und-Größe angegeben. Das dynamische Fenster wird vorübergehend gemacht, was darauf hinweist, dass es beim Start nicht erstellt wird. Dadurch wird ein `DontForceCreate` Wert im `ToolWindows` Schlüssel in der Systemregistrierung geschrieben. Weitere Informationen finden Sie unter [Konfiguration der Tool Fenster Anzeige](../vs-2015/extensibility/tool-window-display-configuration.md?view=vs-2015).