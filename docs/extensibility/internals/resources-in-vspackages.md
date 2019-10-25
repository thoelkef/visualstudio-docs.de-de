---
title: Ressourcen in VSPackages | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07e1e19f802203b9770764330ea894b7d0eb98b8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724153"
---
# <a name="resources-in-vspackages"></a>Ressourcen in VSPackages
Sie können lokalisierte Ressourcen in Native Satelliten-UI-DLLs, verwaltete Satelliten-DLLs oder in ein verwaltetes VSPackage einbinden.

 Einige Ressourcen können nicht in VSPackages eingebettet werden. Die folgenden verwalteten Typen können eingebettet werden:

- Zeichenfolgen

- Paket Lade Schlüssel (auch Zeichen folgen)

- Tool Fenster Symbole

- Dateien für die kompilierte Befehls Tabellenausgabe (CTO)

- CTO-Bitmaps

- Befehlszeilen Hilfe

- Informationen zu Dialogfeld Daten

  Ressourcen in einem verwalteten Paket werden anhand der Ressourcen-ID ausgewählt. Eine Ausnahme ist die CTO-Datei, die mit dem Namen "ctmenu" benannt werden muss. Die CTO-Datei muss als `byte[]` in der Ressourcen Tabelle angezeigt werden. Alle anderen Ressourcen Elemente werden nach Typ identifiziert.

  Sie können das <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>-Attribut verwenden, um anzugeben, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], welche verwalteten Ressourcen verfügbar sind.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  Wenn <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> auf diese Weise festgelegt wird, bedeutet dies, dass [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bei der Suche nach Ressourcen, z. b. durch <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>, nicht verwaltete Satelliten-DLLs ignorieren sollten. Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zwei oder mehr Ressourcen ermittelt, die dieselbe Ressourcen-ID aufweisen, wird die erste gefundene Ressource verwendet.

## <a name="example"></a>Beispiel
 Das folgende Beispiel ist eine verwaltete Darstellung eines Tool Fenster Symbols.

```
<data name="1001"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyToolWinIcon.bmp;
     System.Drawing.Bitmap,
     System.Drawing,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

 Im folgenden Beispiel wird veranschaulicht, wie das CTO-Bytearray einbettet wird, das als ctmenu benannt werden muss.

```
<data name="CTMENU"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyPackage.cto;
     System.Byte[],
     mscorlib,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

## <a name="implementation-notes"></a>Implementierungs Hinweise
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verzögert das Laden von VSPackages, wann immer dies möglich ist. Eine Folge der Einbettung einer CTO-Datei in ein VSPackage ist, dass [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] während des Setups alle VSPackages in den Arbeitsspeicher laden muss. Dies ist der Fall, wenn eine zusammengeführte Befehls Tabelle erstellt wird. Ressourcen können aus einem VSPackage extrahiert werden, indem die Metadaten untersucht werden, ohne dass Code im VSPackage ausgeführt wird. Das VSPackage ist zu diesem Zeitpunkt nicht initialisiert, sodass der Leistungsverlust minimal ist.

 Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nach dem Setup eine Ressource von einem VSPackage anfordert, wird dieses Paket wahrscheinlich bereits geladen und initialisiert, sodass der Leistungsverlust minimal ist.

## <a name="see-also"></a>Siehe auch
- [Verwalten von VSPackages](../../extensibility/managing-vspackages.md)
- [Lokalisierte Ressourcen in MFC-Anwendungen: Satelliten-DLLs](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
