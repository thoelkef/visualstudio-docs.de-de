---
title: VSIX Farb-Compiler | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f414a56bb05a23b6efef19aa7c99292b8a40038a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703899"
---
# <a name="vsix-color-compiler"></a>VSIX-Farbcompiler
Das Visual Studio Extension Color Compiler-Tool ist eine Konsolenanwendung, die eine XML-Datei, die Farben für vorhandene Visual Studio-Designs darstellt, in eine Pkgdef-Datei verdeckt, sodass diese Farben in Visual Studio verwendet werden können. Da es einfach ist, Unterschiede zwischen .xml-Dateien zu vergleichen, ist dieses Tool nützlich für die Verwaltung benutzerdefinierter Farben in der Quellcodeverwaltung. Es kann auch in Build-Umgebungen eingebunden werden, so dass die Ausgabe des Builds eine gültige .pkgdef-Datei ist.

 **Design-XML-Schema**

 Eine vollständige Theme .xml Datei sieht wie folgt aus:

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

 Das \<Design->-Element definiert ein ganzes Design. Ein Design muss mindestens \<ein Kategorie->-Element enthalten. Themenelemente sind wie folgt definiert:

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|||
|-|-|
|**attribute**|**Definition**|
|name|[Erforderlich] Der Name des Themas|
|GUID|[Erforderlich] Die GUID des Themas (muss mit der GUID-Formatierung übereinstimmen)|

 Beim Erstellen benutzerdefinierter Farben für Visual Studio müssen diese Farben für die folgenden Designs definiert werden. Wenn für ein bestimmtes Design keine Farben vorhanden sind, versucht Visual Studio, die fehlenden Farben aus dem Light-Design zu laden.

|||
|-|-|
|**Themenname**|**Thema GUID**|
|Leicht|De3dbbcd-f642-433c-8353-8f1df4370aba|
|Dark|Nr. 1ded0138-47ce-435e-84ef-9ec1f439b749|
|Blau|A4d6a176-b948-4b29-8c66-53c97a1ed7d0|
|Hoher Kontrast|A4d6a176-b948-4b29-8c66-53c97a1ed7d0|

 **Kategorie**

 Das \<Element Kategorie> definiert eine Sammlung von Farben in einem Design. Kategorienamen stellen logische Gruppierungen bereit und sollten so eng wie möglich definiert werden. Eine Kategorie muss mindestens \<ein Color>-Element enthalten. Kategorieelemente werden wie folgt definiert:

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|||
|-|-|
|**attribute**|**Definition**|
|name|[Erforderlich] Der Name der Kategorie|
|GUID|[Erforderlich] Die GUID der Kategorie (muss mit der GUID-Formatierung übereinstimmen)|

 **Color**

 Das \<>-Element Color definiert eine Farbe für eine Komponente oder einen Zustand der Benutzeroberfläche. Das bevorzugte Benennungsschema für eine Farbe ist [UI-Typ] [Status]. Verwenden Sie das Wort "Farbe" nicht, da es redundant ist. Eine Farbe sollte deutlich den Elementtyp und die Situationen oder den "Zustand" angeben, auf den die Farbe angewendet wird. Eine Farbe darf nicht leer sein und muss \<entweder einen \<oder beide eines Background->- und Vordergrund->-Elements enthalten. Farbelemente sind wie folgt definiert:

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|||
|-|-|
|**attribute**|**Definition**|
|name|[Erforderlich] Der Name der Farbe|

 **Hintergrund und/oder Vordergrund**

 Die \<> \<Elemente Background> und Vordergrund definieren den Wert und Typ einer Farbe für den Hintergrund oder den Vordergrund eines UI-Elements. Diese Elemente haben keine Kinder.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|||
|-|-|
|**attribute**|**Definition**|
|type|[Erforderlich] Der Typ der Farbe. Folgende Werte sind möglich:<br /><br /> *CT_INVALID:* Die Farbe ist ungültig oder nicht festgelegt.<br /><br /> *CT_RAW:* Ein roher ARGB-Wert.<br /><br /> *CT_COLORINDEX:* NICHT VERWENDEN.<br /><br /> *CT_SYSCOLOR:* Eine Windows-Systemfarbe von SysColor.<br /><br /> *CT_VSCOLOR:* Eine Visual Studio-Farbe aus __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* Die automatische Farbe.<br /><br /> *CT_TRACK_FOREGROUND:* NICHT VERWENDEN.<br /><br /> *CT_TRACK_BACKGROUND:* NICHT VERWENDEN.|
|`Source`|[Erforderlich] Der Wert der Farbe, die in hexadezimal dargestellt wird|

 Alle Werte, die von der __VSCOLORTYPE-Enumeration unterstützt werden, werden vom Schema im Type-Attribut unterstützt. Es wird jedoch empfohlen, nur CT_RAW und CT_SYSCOLOR zu verwenden.

 **Alle zusammen**

 Dies ist ein einfaches Beispiel für eine gültige Design .xml-Datei:

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

## <a name="how-to-use-the-tool"></a>Verwendung des Tools
 **Syntax**

 VsixColorCompiler \<XML-Datei> \<PkgDef-Datei> \<optionale Args>

 **Argumente**

||||
|-|-|-|
|**Switch-Name**|**Hinweise**|**Erforderlich oder Optional**|
|Unbenannt (.xml-Datei)|Dies ist der erste unbenannte Parameter und ist der Pfad zur zu konvertierenden XML-Datei.|Erforderlich|
|Unbenannt (.pkgdef-Datei)|Dies ist der zweite unbenannte Parameter und ist der Ausgabepfad für die generierte .pkgdef-Datei.<br /><br /> Standard: \<XML-Dateiname>.pkgdef|Optional|
|/noLogo|Durch das Setzen dieses Flags werden Produkt- und Copyrightinformationen nicht mehr gedruckt.|Optional|
|/?|Drucken Sie Hilfeinformationen aus.|Optional|
|/help|Drucken Sie Hilfeinformationen aus.|Optional|

 **Beispiele**

- VsixColorCompiler D:-xml-farben.xml-D:-pkgdef-Colors.pkgdef

- VsixColorCompiler D:-xml-farben.xml /noLogo

## <a name="notes"></a>Notizen

- Dieses Tool erfordert die Installation der neuesten Version der VC++-Laufzeit.

- Es werden nur einzelne Dateien unterstützt. Die Massenkonvertierung über Ordnerpfade wird nicht unterstützt.

## <a name="sample-output"></a>Beispielausgabe
 Die vom Tool generierte .pkgdef-Datei ähnelt den folgenden Tasten:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
