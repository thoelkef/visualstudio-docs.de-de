---
title: Gliederung im ein Legacy-Sprachdienst | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b899f53ba6b2a0b58997cc51a83a0d9ca8480e63
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135650"
---
# <a name="outlining-in-a-legacy-language-service"></a>Gliederung im ein Legacy-Sprachdienst
Gliederung erleichtert möglich, ein komplexes Programm in eine Übersicht über oder Gliederung zu reduzieren. In c# können z. B. alle Methoden einer einzelnen Zeile eine zeigt nur die Methodensignatur reduziert werden. Darüber hinaus können Strukturen und Klassen reduziert werden, um nur die Namen der Strukturen und Klassen angezeigt. Innerhalb einer einzelnen Methode, eine komplexe Logik reduziert werden kann, um den Gesamtablauf anzuzeigen nur die erste Zeile von Anweisungen wie z. B. `foreach`, `if`, und `while`.  
  
 Dienste für Legacy-Sprachen werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Dienstfunktionen Sprache ist die Verwendung von MEF-Erweiterungen. Wenn Sie mehr erfahren möchten, finden Sie unter [Exemplarische Vorgehensweise: Gliedern](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor API so bald wie möglich verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="enabling-support-for-outlining"></a>Aktivieren der Unterstützung für eine Gliederung  
 Die `AutoOutlining` Registrierungseintrag auf 1 festgelegt ist, um die automatische Gliederung zu aktivieren. Automatische Gliederung richtet eine Analyse der gesamten Quelle beim eine Datei geladen wird, oder geändert, um ausgeblendete Bereiche zu identifizieren und die Symbole Gliederungsmodus anzeigen. Gliederung kann auch manuell vom Benutzer gesteuert werden.  
  
 Der Wert des der `AutoOutlining` Registrierungseintrag abgerufen werden kann, durch die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> Eigenschaft auf die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse. Die `AutoOutlining` Registrierungseintrag kann initialisiert werden, durch eine benannte Parameter, um die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Attribut (finden Sie unter [registrieren einen Sprachdienst Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md) Einzelheiten).  
  
## <a name="the-hidden-region"></a>Die ausgeblendeten Bereich  
 Um Gliederung zu gewährleisten, muss der Sprachdienst ausgeblendete Bereiche unterstützen. Hierbei handelt es sich um eine Passage mit Text, der erweitert oder reduziert werden können. Ausgeblendete Bereiche können durch Standardsprache Symbole, z. B. geschweifte Klammern oder durch benutzerdefinierte Symbole begrenzt sein. Hat z. B. c# eine `#region` / `#endregion` -Paar, das einen ausgeblendeten Bereich begrenzt.  
  
 Ausgeblendete Bereiche werden von einem ausgeblendeten Region-Manager, die als zugänglich ist verwaltet die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Schnittstelle.  
  
 Ausgeblendete Bereiche Gliederung verwendet die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> -Schnittstelle und enthalten die Spanne der ausgeblendeten Bereich, den aktuellen Sichtbarkeitsstatus und Banner angezeigt werden, wenn die Spanne reduziert ist.  
  
 Die sprachdienstparser verwendet die <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> -Methode zum Hinzufügen einer neuen ausgeblendeten Region mit das Standardverhalten für ausgeblendete Bereiche während der <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> Methode können Sie das Aussehen und Verhalten der Kontur anpassen. Sobald ausgeblendete Bereiche der Sitzung ausgeblendeten Bereich zugewiesen werden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ausgeblendete Bereiche für das Language-Dienst verwaltet.  
  
 Wenn Sie müssen bestimmen, wann die Sitzung ausgeblendeten Bereich zerstört wird, ein ausgeblendeten Bereich geändert wird, oder müssen Sie sicherstellen, dass ein bestimmter ausgeblendeter Bereich sichtbar ist; Leiten Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.Source> Klasse, und überschreiben Sie die entsprechenden Methoden <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, und <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>zugeordnet.  
  
### <a name="example"></a>Beispiel  
 Hier ist ein vereinfachtes Beispiel einer erstellen ausgeblendete Bereiche für alle Paare von geschweiften Klammern ein. Es wird davon ausgegangen, dass die Sprache bereitstellt, Zuordnung von geschweiften Klammern, und dass die geschweiften Klammern, die abgeglichen werden mindestens die geschweiften Klammern enthalten ({und}). Dieser Ansatz ist nur zur Veranschaulichung. Eine vollständige Implementierung müsste eine vollständige Behandlung der Fälle im <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. Dieses Beispiel zeigt auch zum Festlegen der <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> Vorrang `true` vorübergehend. Eine Alternative ist die Angabe der `AutoOutlining` benannter Parameter in der `ProvideLanguageServiceAttribute` Attribut im Language-Paket.  
  
 In diesem Beispiel geht davon aus C#-Regeln für Kommentare, Zeichenfolgen und Literale.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
  
    public class MyLanguageService : LanguageService  
    {  
        private LanguagePreferences m_preferences;  
  
        public override LanguagePreferences  GetLanguagePreferences()  
        {  
            if (m_preferences == null)  
            {  
                m_preferences = new LanguagePreferences(this.Site,  
                                                        typeof(MyLanguageService).GUID,  
                                                        Name);  
                m_preferences.Init();  
                // Temporarily enabled auto-outlining  
                m_preferences.AutoOutlining = true;  
            }  
            return m_preferences;  
        }  
  
        public override AuthoringScope  ParseSource(ParseRequest req)  
        {  
            Source source = (Source) this.GetSource(req.FileName);  
            switch (req.Reason)  
            {  
               case ParseReason.HighlightBraces:  
               case ParseReason.MatchBraces:  
               case ParseReason.MemberSelectAndHighlightBraces:  
                  if (source.Braces != null)  
                  {  
                      foreach (TextSpan[] brace in source.Braces)  
                      {  
                         if (brace.Length == 2)  
                         {  
                             if (req.Sink.HiddenRegions == true   
                                   && source.GetText(brace[0]).Equals("{")   
                                   && source.GetText(brace[1]).Equals("}"))  
                             {  
                                //construct a TextSpan of everything between the braces  
                                TextSpan hideSpan = new TextSpan();  
                                hideSpan.iStartIndex = brace[0].iStartIndex;  
                                hideSpan.iStartLine = brace[0].iStartLine;  
                                hideSpan.iEndIndex = brace[1].iEndIndex;  
                                hideSpan.iEndLine = brace[1].iEndLine;  
                                req.Sink.ProcessHiddenRegions = true;  
                                req.Sink.AddHiddenRegion(hideSpan);  
                             }  
                             req.Sink.MatchPair(brace[0], brace[1], 1);  
                         }  
                         else if (brace.Length >= 3)  
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);  
                  }  
        }  
                   break;  
               default:  
                   break;  
      }  
            // Must always return a valid AuthoringScope object.  
            return new MyAuthoringScope();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Legacy-Dienst-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrieren einen Sprachdienst Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)