---
title: Versionsnummern für Hauptassemblys und lokalisierte Satellitenassemblys
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cbc74d746453c5d8e60161004a5b56a2c21915dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882597"
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Versionsnummern für Hauptassemblys und lokalisierte Satellitenassemblys
Die <xref:System.Resources.SatelliteContractVersionAttribute>-Klasse bietet Unterstützung bei der Versionsverwaltung für eine Hauptassembly, die lokalisierte Ressourcen mithilfe des Ressourcen-Managers verwendet. Das Anwenden von <xref:System.Resources.SatelliteContractVersionAttribute> auf die Hauptassembly einer Anwendung ermöglicht es Ihnen, die Assembly zu aktualisieren und erneut bereitzustellen, ohne die Satellitenassemblys zu aktualisieren. Beispielsweise können Sie die <xref:System.Resources.SatelliteContractVersionAttribute>-Klasse mit einem Service Pack verwenden, das keine neuen Ressourcen einbringt, ohne die Satellitenassemblys neu zu erstellen und erneut bereitzustellen. Damit Ihre lokalisierten Ressourcen zur Verfügung stehen, muss die Satellitenvertragsversion der Hauptassembly mit der <xref:System.Reflection.AssemblyVersionAttribute>-Klasse der Satellitenassemblys übereinstimmen. Geben Sie eine genaue Versionsnummer in <xref:System.Resources.SatelliteContractVersionAttribute> an. Platzhalterzeichen wie „*“ sind ungültig. Weitere Informationen finden Sie unter [Abrufen von Ressourcen](/dotnet/framework/resources/retrieving-resources-in-desktop-apps).

## <a name="update-assemblies"></a>Aktualisieren von Assemblys
 Mit der <xref:System.Resources.SatelliteContractVersionAttribute>-Klasse können Sie eine Hauptassembly aktualisieren, ohne die Satellitenassembly aktualisieren zu müssen oder umgekehrt. Wenn die Hauptassembly aktualisiert wird, wird die Versionsnummer der Assembly geändert. Wenn Sie weiterhin die vorhandenen Satellitenassemblys verwenden möchten, ändern Sie die Versionsnummer der Hauptassembly, aber lassen Sie die Versionsnummer des Satellitenvertrags unverändert. Beispielsweise kann die Hauptassemblyversion im ersten Release 1.0.0.0 sein. Die Satellitenvertragsversion und die Assemblyversion der Satellitenassembly werden ebenfalls 1.0.0.0 sein. Wenn Sie die Hauptassembly für ein Service Pack aktualisieren müssen, können Sie die Assemblyversion zu 1.0.0.1 ändern, während Sie für die Satellitenvertragsversion und die Satellitenassemblyversion 1.0.0.0 beibehalten.

 Wenn Sie eine Satellitenassembly, jedoch nicht die Hauptassembly aktualisieren müssen, ändern Sie die <xref:System.Reflection.AssemblyVersionAttribute> der Satellitenassembly. Zusammen mit der Satellitenassembly müssen Sie eine Richtlinienassembly bereitstellen, die besagt, dass die neue Satellitenassembly mit der alten Satellitenassembly kompatibel ist. Weitere Informationen zu Richtlinien finden Sie unter [So sucht Common Language Runtime nach Assemblys](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

 Im folgenden Codebeispiel wird veranschaulicht, wie die Satellitenvertragsversion festgelegt wird. Der Code kann in ein Buildskript, die *AssemblyInfo.vb*-Datei oder die *AssemblyInfo.cs*-Datei eingefügt werden.

```vb
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>
```

```csharp
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]
```

## <a name="see-also"></a>Siehe auch

- [So sucht Common Language Runtime nach Assemblys](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)
- [Festlegen von Assemblyattributen](/dotnet/framework/app-domains/set-assembly-attributes)
- [Sicherheit und lokalisierte Satellitenassemblys](../ide/security-and-localized-satellite-assemblies.md)
- [Lokalisieren von Anwendungen](../ide/localizing-applications.md)
- [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)