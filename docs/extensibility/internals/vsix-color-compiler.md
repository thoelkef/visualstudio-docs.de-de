---
title: VSIX-Farbe Compiler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 115f3a6c9d01d1e92a5eb7c840dfb17abcfd3c72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="vsix-color-compiler"></a>Die Farbe Compiler VSIX
Das Visual Studio-Erweiterung Farbe Compiler-Tool ist eine Konsolenanwendung, die eine XML-Datei, die Farben für vorhandene Visual Studio-Designs darstellt akzeptiert und wandelt es eine PKGDEF-Datei, damit diese Farben in Visual Studio verwendet werden können. Da es Unterschiede zwischen XML-Dateien einfach ist, eignet sich dieses Tool zum Verwalten von benutzerdefinierten Farben in der quellcodeverwaltung. Es kann auch in Buildumgebungen eingebunden werden soll, sodass die Ausgabe des Builds eine gültige PKGDEF-Datei ist.  
  
 **Design XML-schema**  
  
 Eine vollständige Design-XML-Datei sieht wie folgt:  
  
```xml  
<Themes>  
      <!—one or Theme elements -->  
      <Theme>  
        <!-- one or more Category elements -->  
        <Category>  
          <!-- one or more Color elements -->  
          <Color>  
            <!-- zero or one Background element -->  
            <Background />  
            <!-- zero or one Foreground element -->  
            <Foreground />  
          </Color>  
        </Category>  
      </Theme>  
</Themes>  
```  
  
 **Design**  
  
 Die \<Design ">-Element definiert ein gesamte Design. Ein Design muss mindestens ein enthalten \<Kategorie > Element. Designelemente werden wie folgt definiert:  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**Attribut**|**Definition**|  
|name|[Erforderlich] Der Name des Designs|  
|GUID|[Erforderlich] Das Design-GUID (müssen mit GUID Formatierung)|  
  
 Wenn Sie benutzerdefinierte Farben für Visual Studio zu erstellen, müssen diese Farben für die folgenden Designs definiert werden. Wenn keine Farben für ein bestimmtes Design vorhanden sind, versucht Visual Studio die fehlenden Farben aus das Design "hell" geladen.  
  
|||  
|-|-|  
|**Name des Designs**|**Design "GUID"**|  
|Hell|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|Dunkel|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|Blau|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|Hoher Kontrast|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **Kategorie**  
  
 Die \<Kategorie >-Element definiert eine Auflistung von Farben in einem Design. Kategorienamen logische Gruppierungen bereitstellen, und sollte als eng wie möglich definiert werden. Eine Kategorie muss mindestens ein enthalten \<Farbe > Element. Kategorie-Elemente werden wie folgt definiert:  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**Attribut**|**Definition**|  
|name|[Erforderlich] Der Name der Kategorie|  
|GUID|[Erforderlich] Die Kategorie-GUID (müssen mit GUID Formatierung)|  
  
 **Farbe**  
  
 Die \<Farbe >-Element definiert eine Farbe für eine Komponente oder der Zustand der Benutzeroberfläche. Die bevorzugte Benennungsschema für eine Farbe ist [Benutzeroberflächentyp] [State]. Verwenden Sie das Wort "Color", wie sie redundant ist. Eine Farbe sollte klar anzugeben, den Elementtyp und die Situationen oder "Bundesland" an, für die die Farbe angewendet werden soll. Eine Farbe darf nicht leer sein und muss entweder eine oder beide der enthalten eine \<Hintergrund > und \<Vordergrund > Element. Farbelemente sind wie folgt definiert:  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|||  
|-|-|  
|**Attribut**|**Definition**|  
|name|[Erforderlich] Der Name der Farbe|  
  
 **Hintergrund und/oder Vordergrund**  
  
 Die \<Hintergrund > und \<Vordergrund >-Elemente definieren einer Farbe Wert und Typ für den Hintergrund oder Vordergrund eines UI-Elements. Diese Elemente verfügen über keine untergeordneten Elemente.  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**Attribut**|**Definition**|  
|Typ|[Erforderlich] Der Typ der ausgewählten Farbe. Es kann einer der folgenden sein:<br /><br /> *CT_INVALID:* die Farbe ist ungültig oder nicht festgelegt.<br /><br /> *CT_RAW:* ARGB-Rohwert.<br /><br /> *CT_COLORINDEX:* NICHT VERWENDEN.<br /><br /> *CT_SYSCOLOR:* eine Windows-System-Farbe von SysColor.<br /><br /> *CT_VSCOLOR:* aus __VSSYSCOLOREX eine Visual Studio-Farbe.<br /><br /> *CT_AUTOMATIC:* die automatische Färbung.<br /><br /> *CT_TRACK_FOREGROUND:* NICHT VERWENDEN.<br /><br /> *CT_TRACK_BACKGROUND:* NICHT VERWENDEN.|  
|Quelle|[Erforderlich] Der Wert der Farbe im hexadezimalen Format dargestellt wird.|  
  
 Alle Werte, die von der Aufzählung __VSCOLORTYPE unterstützt werden nach dem Schema in das Type-Attribut unterstützt. Allerdings wird empfohlen, dass Sie nur CT_RAW und CT_SYSCOLOR verwenden.  
  
 **Alle zusammen**  
  
 Dies ist ein einfaches Beispiel einer gültigen Design-XML-Datei:  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">  
      <Color Name="MyActiveBorder">  
        <Background Type="CT_RAW" Source="FFCCCEDB" />  
      </Color>  
    </Category>  
  </Theme>  
</Themes>  
```  
  
## <a name="how-to-use-the-tool"></a>Gewusst wie: Verwenden Sie das tool  
 **Syntax**  
  
 VsixColorCompiler \<XML-Datei > \<PkgDef-Datei > \<Optional Args >  
  
 **Argumente**  
  
||||  
|-|-|-|  
|**SwitchName**|**Notizen**|**Erforderlich oder Optional**|  
|Unbenannte (XML-Datei)|Dies ist der erste unbenannte Parameter und den Pfad der XML-Datei konvertiert wird.|Erforderlich|  
|Unbenannte (PKGDEF-Datei)|Dies ist der zweite unbenannte Parameter und den Ausgabepfad für die generierte PKGDEF-Datei.<br /><br /> Standard: \<XML-Dateiname > PKGDEF|Optional|  
|/noLogo|Dieses Flag hält Produkt- und Copyright-Informationen drucken.|Optional|  
|/?|Drucken Sie Hilfeinformationen.|Optional|  
|/help|Drucken Sie Hilfeinformationen.|Optional|  
  
 **Beispiele**  
  
-   VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
-   VsixColorCompiler D:\xml\colors.xml/nologo  
  
## <a name="notes"></a>Hinweise  
  
-   Dieses Tool erfordert, dass die neueste Version der VC++-Laufzeit installiert werden.  
  
-   Nur einzelne Dateien werden unterstützt. Das massenkonvertieren über Ordnerpfaden wird nicht unterstützt.  
  
## <a name="sample-output"></a>Beispielausgabe:  
 Die PKGDEF-Datei, die vom Tool generierte werden ähnlich den folgenden Schlüssel:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```