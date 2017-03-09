---
title: "Gewusst wie: Kennzeichnen eines VSPackages (C# und Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Info (Dialogfeld)"
  - "VSPackages, Begrüßungsbildschirme"
  - "VSPackages, Branding"
ms.assetid: 705a41c3-63d6-4c1e-9f82-771be9191579
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Gewusst wie: Kennzeichnen eines VSPackages (C# und Visual Basic)
Um Informationen im Dialogfeld und im Begrüßungsbildschirm angezeigt wird, muss die VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>\-Schnittstelle implementieren.  Dadurch werden die folgenden Informationen zu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]bereit:  
  
-   Name  
  
-   ID, wie Serie oder Versionsnummer  
  
-   Information  
  
-   Symbol für das Logo  
  
 Der folgende Code besteht aus [VSSDK\-Beispiele](../misc/vssdk-samples.md).  
  
### So implementieren IVsInstalledProduct\-Schnittstelle  
  
1.  Fügen Sie das <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute>\-Attribut der Klasse hinzu, die einem VSPackage implementieren.  Diese Klasse muss von <xref:Microsoft.VisualStudio.Shell.Package> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>berechnen.  
  
     [!code-cs[VSSDKPackageSplashHelpAboutLoadKey#1](../misc/codesnippet/CSharp/how-to-brand-a-vspackage-csharp-and-visual-basic_1.cs)]
     [!code-vb[VSSDKPackageSplashHelpAboutLoadKey#1](../misc/codesnippet/VisualBasic/how-to-brand-a-vspackage-csharp-and-visual-basic_1.vb)]  
  
     Das erste Argument, <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute.UseInterface%2A>, <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> des Attributs wird [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] an, <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> verwenden, um Produktinformationen, anstatt des InstalledProducts\-Registrierungsschlüssels abzurufen.  Die übrigen Argumente Zeichenfolgenressourcen Option aus, um den Produktnamen, die ID und den Details anzuzeigen.  Da das erste Argument `true`ist, sind die übrigen Argumente `null`.  
  
2.  Klicken Sie mit der rechten Maustaste auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>, zeigen Sie auf **Schnittstelle implementieren**, und klicken Sie dann auf **Schnittstelle implementieren**.  
  
3.  Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> mithilfe des folgenden Codes.  
  
     [!code-cs[VSSDKPackageSplashHelpAboutLoadKey#2](../misc/codesnippet/CSharp/how-to-brand-a-vspackage-csharp-and-visual-basic_2.cs)]
     [!code-vb[VSSDKPackageSplashHelpAboutLoadKey#2](../misc/codesnippet/VisualBasic/how-to-brand-a-vspackage-csharp-and-visual-basic_2.vb)]  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ruft diese Methode auf, um Einbrennen Informationen zum Abrufen von VSPackages.  Die GetResourceString\-Methode wird verwendet, um diese Informationen zu isolieren.  
  
    > [!NOTE]
    >  Codekommentare werden der Kürze halber gelöscht.  Sie können sie in [VSSDK\-Beispiele](../misc/vssdk-samples.md)suchen.  
  
### Um die Produktinformations Beibehalten von Zeichenfolgen  
  
1.  Doppelklicken Sie auf die .resx\-Ressourcendatei, die mit einem VSPackage zugeordnet ist.  
  
     Der Ressourcen\-Editor wird geöffnet.  
  
2.  Suchen, oder fügen Sie den Produktnamen, die Informationen und die ID hinzu  
  
     Die folgenden Ressourcenzeichenfolgen sind von [VSSDK\-Beispiele](../misc/vssdk-samples.md).  
  
     @101  
     Paket\-Begrüßungsbildschirm und Hilfe zu den offiziellen Namen \(C\#\).  
  
     @102  
     Dieses Paket wird veranschaulicht, wie Text und Bild im Begrüßungsbildschirm und ungefähr in der Hilfe angezeigt wird.  
  
     @104  
     8.0  
  
3.  Wählen Sie aus, und bearbeiten Sie diese Informationen, wie Sie möchten.  
  
### Um die Produkt Bitmaps und Symbole beibehalten  
  
1.  Fügen Sie die Bitmaps und Symbole als Projektressourcen dem Projekt hinzu.  
  
     Weitere Informationen finden Sie unter [NOT IN BUILD: Adding and Editing Resources \(Visual C\#\)](http://msdn.microsoft.com/de-de/95f15d03-bed0-410c-8d1f-dece5199ba1e).  
  
2.  Schließen Sie den Ressourcen\-Editor, und öffnen Sie die RESX\-Datei in einem XML\- oder in einem Texteditor.  
  
    > [!NOTE]
    >  Der Ressourcen\-Editor unterstützt das Zuweisen von Ressource ID auf die Elemente nichts anderes als Zeichenfolgen.  
  
3.  Suchen oder fügen Sie das Symbol und die Bitmapressourcen der RESX\-Datei hinzu.  Die folgenden Ressourcen sind von [VSSDK\-Beispiele](../misc/vssdk-samples.md).  
  
    ```  
    <data name="300" type="System.Resources.ResXFileRef, System.Windows.Forms">  
        <value>GenericPackage.bmp;System.Drawing.Bitmap, System.Drawing,  
            Version=2.0.0.0, Culture=neutral,         PublicKeyToken=b03f5f7f11d50a3a</value>  
    </data>  
    <data name="400" type="System.Resources.ResXFileRef, System.Windows.Forms">  
        <value>GenericPackage.ico;System.Drawing.Icon, System.Drawing,  
            Version=2.0.0.0, Culture=neutral,         PublicKeyToken=b03f5f7f11d50a3a</value>  
    </data>  
    ```  
  
### Um das Dialogfeld Info Begrüßungsbildschirme und testen  
  
-   Um ein VSPackage zu testen, finden Sie unter [Gewusst wie: Testen von „Hilfe zu“ und Begrüßungsbildschirmen](../misc/how-to-test-the-help-about-and-splash-screens.md).  
  
## Siehe auch  
 [Branding von VSPackages](../misc/vspackage-branding.md)