## 2D Graphics Libraries

### TASImage

-   In some cases dashed lines with a line width greater than "1" were
    not drawn.
-   The `TLatex` symbol `#tilde`, was misplaced.

### X11 fonts

-   A coverity fix in `Rotated.cxx` had a side effect on rotated text
    drawn with X11 fonts.

### TCanvas

- 'TPad::SaveAs' produces named macros in .C files.

### TGaxis and TAxis

-   The time axis behavior should now be correct along time zone and
    summer saving time. A fix has been done with the of Philippe Gras
    (CEA Saclay. IRFU/SEDI) and Julian Sitarek (IFAE). Time axis
    transported from a time zone to an other in a ROOT file are correct
    too. A new example test have been introduced to test the time axis
    (timeonaxis3.C)

### TLegend

-   The line attribute of objects in the legend were not taken into
    account with the option "e".

### TPie

-   New drawing option "SC" to draw the labels with the slices' colors.

### TMathText

-   TMathText's purpose is to write mathematical equations, exactly as
    TeX would do it. The syntax is the same as the TeX's one. Author:
    Yue Shi Lai (MIT)) \
    Example:

``` {.cpp}
    {
       TMathText l;
       l.SetTextAlign(23);
       l.SetTextSize(0.06);
       l.DrawMathText(0.50, 1.000, "\\prod_{j\\ge0} \\left(\\sum_{k\\ge0} a_{jk}z^k\\right) = \\sum_{n\\ge0} z^n \\left(\\sum_{k_0,k_1,\\ldots\\ge0\\atop k_0+k_1+\\cdots=n} a_{0k_0}a_{1k_1} \\cdots \\right)");
       l.DrawMathText(0.50, 0.800, "W_{\\delta_1\\rho_1\\sigma_2}^{3\\beta} = U_{\\delta_1\\rho_1\\sigma_2}^{3\\beta} + {1\\over 8\\pi^2} \\int_{\\alpha_1}^{\\alpha_2} d\\alpha_2^\\prime \\left[ {U_{\\delta_1\\rho_1}^{2\\beta} - \\alpha_2^\\prime U_{\\rho_1\\sigma_2}^{1\\beta} \\over U_{\\rho_1\\sigma_2}^{0\\beta}} \\right]");
       l.DrawMathText(0.50, 0.600, "d\\Gamma = {1\\over 2m_A} \\left( \\prod_f {d^3p_f\\over (2\\pi)^3} {1\\over 2E_f} \\right) \\left| \\mathscr{M} \\left(m_A - \\left\\{p_f\\right\\} \\right) \\right|^2 (2\\pi)^4 \\delta^{(4)} \\left(p_A - \\sum p_f \\right)");
       l.DrawMathText(0.50, 0.425, "4\\mathrm{Re}\\left\\{{2\\over 1-\\Delta\\alpha} \\chi(s) \\left[ \\^{g}_\\nu^e \\^{g}_\\nu^f (1 + \\cos^2\\theta) + \\^{g}_a^e \\^{g}_a^f \\cos\\theta \\right] \\right\\}");
       l.DrawMathText(0.50, 0.330, "p(n) = {1\\over\\pi\\sqrt{2}} \\sum_{k = 1}^\\infty \\sqrt{k} A_k(n) {d\\over dn} {\\sinh \\left\\{ {\\pi\\over k} \\sqrt{2\\over 3} \\sqrt{n - {1\\over 24}} \\right\\} \\over \\sqrt{n - {1\\over 24}}}");
       l.DrawMathText(0.13, 0.150, "{(\\ell+1)C_{\\ell}^{TE} \\over 2\\pi}");
       l.DrawMathText(0.27, 0.110, "\\mathbb{N} \\subset \\mathbb{R}");
       l.DrawMathText(0.63, 0.100, "\\hbox{RHIC スピン物理 Нью-Йорк}");
    }
```

   ![TMathText example](mathtext.png "TMathText example")

### TLatex

-   The class `TMathText` is a TeX math formulae interpreter. It uses
    plain TeX syntax and uses "\\" as control instead of "\#". If a
    piece of text containing "\\" is given to `TLatex` then `TMathText`
    is automatically invoked. Therefore, as histograms' titles, axis
    titles, labels etc ... are drawn using `TLatex`, the `TMathText`
    syntax can be used for them also.
-   Fix a very old bug (in `TTF.cxx` since the beginning). With the
    following code the spaces between "text" and \#lambda were ignored.

``` {.cpp}
       TLatex t; t.DrawLatex( 0.1,0.1,"text   #Lambda" )
```

-   Implement `#backslash`.

