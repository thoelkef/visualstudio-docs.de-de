---
title: Ressourcen in VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d252f61a9f634f4bb8435626c41c586bbe5cb839
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130949"
---
# <a name="resources-in-vspackages"></a>Ressourcen in VSPackages
Sie können die lokalisierte Ressourcen in systemeigenen-Satelliten-DLLs der Benutzeroberfläche, verwaltete Satelliten-DLLs oder in ein verwaltetes VSPackage selbst einbetten.  
  
 Einige Ressourcen können nicht in VSPackages eingebettet werden. Die folgenden verwalteten Typen können eingebettet werden:  
  
-   Zeichenfolgen  
  
-   Paketladeschlüssel (die auch Zeichenfolgen sind)  
  
-   Symbole für Fenster  
  
-   Kompilierte Befehl Tabelle Ausgabe (CTO)-Dateien  
  
-   CTO bitmaps  
  
-   Hilfe zur Befehlszeile  
  
-   Informationen zu Dialogfelddaten  
  
 Ressourcen-ID werden Ressourcen in einem verwalteten Paket ausgewählt. Eine Ausnahme ist der CTO-Datei, die CTMENU genannt werden muss. Die CTO-Datei muss angezeigt werden, in der Ressourcentabelle als eine `byte[]`. Alle anderen Elemente werden nach Typ identifiziert.  
  
 Sie können die <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> Attribut, um anzugeben, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , dass die verwaltete Ressourcen verfügbar sind.  
  
 [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
 [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
 Festlegen von <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> auf diese Weise gibt an, dass [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nicht verwalteten Satelliten-DLLs sollten ignoriert werden, bei der Ressourcen, z. B. mit Suche nach <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] erkennt zwei oder mehr Ressourcen, die über die gleichen Ressourcen-ID, verwendet die erste Ressource gefunden.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird eine verwaltete Darstellung einer Fenster Werkzeugsymbol.  
  
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
  
 Im folgenden Beispiel wird veranschaulicht, wie das Bytearray CTO einbetten, das CTMENU benannt werden muss.  
  
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
  
## <a name="implementation-notes"></a>Hinweise zur Implementierung  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verzögert das Laden von VSPackages, wann immer möglich. Eine Folge der Einbettung einer CTO-Datei in einem VSPackage ist, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] alle solche VSPackages im Arbeitsspeicher muss geladen werden, während des Setups der ist, wenn es sich um eine zusammengeführte Befehlstabelle erstellt. Ressourcen können aus einem VSPackage extrahiert werden, durch die Metadaten ohne Ausführen von Code im VSPackage untersuchen. Das VSPackage wird zu diesem Zeitpunkt nicht initialisiert werden, so den Leistungsabfall minimal ist.  
  
 Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fordert eine Ressource aus einem VSPackage nach der Installation, das Paket ist wahrscheinlich bereits geladen und initialisiert werden, so den Leistungsabfall minimal ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von VSPackages](../../extensibility/managing-vspackages.md)   
 [Lokalisierte Ressourcen in MFC-Anwendungen: Satelliten-DLLs](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)   
