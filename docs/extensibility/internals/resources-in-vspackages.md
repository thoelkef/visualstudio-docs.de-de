---
title: Ressourcen in VSPackages | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 184642501b9452566a15e1aba30312e17500f7bb
ms.lasthandoff: 02/22/2017

---
# <a name="resources-in-vspackages"></a>Ressourcen in VSPackages
Sie können lokalisierte Ressourcen in systemeigenen-Satelliten-DLLs UI, verwalteten Satelliten-DLLs oder in einem verwalteten VSPackage selbst einbetten.  
  
 Einige Ressourcen können nicht in VSPackages eingebettet werden. Die folgenden verwalteten Typen können eingebettet werden:  
  
-   Zeichenfolgen  
  
-   Paketladeschlüssel (die auch Zeichenfolgen)  
  
-   Toolfenstersymbole  
  
-   Kompilierte Befehl Tabelle Ausgabe (CTO)-Dateien  
  
-   CTO von bitmaps  
  
-   Hilfe zur Befehlszeile  
  
-   Informationen zu Dialogfelddaten  
  
 Ressourcen-ID werden Ressourcen in einem verwalteten Paket ausgewählt. Eine Ausnahme ist die Datei CTO CTMENU genannt werden muss. Die CTO-Datei muss angezeigt werden, in der Ressourcentabelle als eine `byte[]`. Alle anderen Elemente werden nach Typ identifiziert.  
  
 Können Sie die <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>Attribut an [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , verwaltete Ressourcen verfügbar sind.</xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>  
  
 [!code-cs[VSSDKResources&#1;](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
 [!code-vb[VSSDKResources Nr.&1;](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
 Festlegen von <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>auf diese Weise gibt an, dass [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nicht verwalteten Satelliten-DLLs sollten ignoriert werden, bei der nach Ressourcen, z. B. Suche mithilfe von <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> </xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zwei oder mehr Ressourcen mit den dieselbe Ressourcen-ID trifft er verwendet die erste Ressource gefunden wird.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird eine verwaltete Darstellung ein Symbol im Fenster.  
  
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
  
 Im folgenden Beispiel wird veranschaulicht, wie das Bytearray CTO einbetten, das CTMENU genannt werden muss.  
  
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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]verzögert Laden von VSPackages, wann immer möglich. Eine Folge der Einbettung einer CTO-Datei in einem VSPackage ist, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] müssen alle diese VSPackages im Arbeitsspeicher während der Installation wird bei der Erstellung einer zusammengeführten Befehlstabelle laden. Untersuchen die Metadaten ohne Ausführen von Code in die VSPackage können Ressourcen aus einem VSPackage extrahiert werden. VSPackage ist zu diesem Zeitpunkt nicht initialisiert werden, damit der Leistungsverlust minimal ist.  
  
 Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fordert eine Ressource aus einem VSPackage nach Abschluss der Installation, das Paket ist wahrscheinlich bereits geladen und initialisiert, der Leistungsverlust minimal.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwaltete VSPackages](../../misc/managed-vspackages.md)   
 [Verwalten von VSPackages](../../extensibility/managing-vspackages.md)   
 [Lokalisierte Ressourcen in MFC-Anwendungen: Satelliten-DLLs](http://msdn.microsoft.com/Library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [Verwaltete VSPackages](../../misc/managed-vspackages.md)
