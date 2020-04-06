---
title: Registrieren eines Toolfensters | Microsoft Docs
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
ms.openlocfilehash: 2e7971de5ae5301d99147bbfc374dda6b039662a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701598"
---
# <a name="register-a-tool-window"></a>Registrieren eines Toolfensters
Sie können Ihre Toolfenster mit <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> und <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>registrieren.

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

 Im obigen Code <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> werden `PersistedWindowPane` die `DynamicWindowPane` und die Toolfenster bei Visual Studio registriert. Das persistente Werkzeugfenster wird mit dem **Projektmappen-Explorer**angedockt und auf die Registerkarte niert, und das dynamische Fenster erhält eine Standardstartposition und -größe. Das dynamische Fenster wird vorübergehend gemacht, was darauf hinweist, dass es beim Start nicht erstellt wird. Dadurch wird `DontForceCreate` ein `ToolWindows` Wert in den Schlüssel in der Systemregistrierung geschrieben. Weitere Informationen finden Sie unter [Symbolfensteranzeigekonfiguration](/visualstudio/extensibility/tool-window-display-configuration?view=vs-2015).
