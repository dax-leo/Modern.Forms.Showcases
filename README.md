# Reall world application example built using Modern.Forms.

# Mobile radio station performance tracker (KPI) and cluster acceptance tool (CAR). Internal application used by Ericsson GmbH, Germany.
Components used: 
- Modern.Forms core library (with some local modifications)
- my own datagrid component (migrated from WinForms)
- ReoGrid - migrated from WinForms
- Epplus - excel generator
- GMAP.NET - migrated from WinForms
- Calendar Drop Down component - port from WinForms
- ScottPlot - port to ModernForms

# Main View
![33747](https://github.com/dax-leo/Modern.Forms.Showcases/assets/70173560/fc02b8d5-f969-4e96-8f7a-a333e4f85a50)

# Report control
![33749](https://github.com/dax-leo/Modern.Forms.Showcases/assets/70173560/bfe7491f-c30e-435e-9ca1-c5987cec8dae)

# Data Analysis and Charts
![33745](https://github.com/dax-leo/Modern.Forms.Showcases/assets/70173560/ca87e24e-0f7e-4183-9345-ad58f2b214f6)

Popup Charts with interactive control (zoom etc.)
![33748](https://github.com/dax-leo/Modern.Forms.Showcases/assets/70173560/0e46fd80-8613-44d4-9b79-31fbad4f7383)

# Conclusion:
- Despite all weak points and missing functionallity I like working with Modern.Forms. Avalonia team did very good job building up base for Avalonia UI. What I don't like is use of WPF/XAML style and overload with so many features, many focused on mobile. In many cases (even for larger business desktop applications) having simple forms with backend Model-View-Presenter approach is perfectly fine. There are many excellent WinForms controls out there. The goal of my repository (Modern.Forms.Toolkit) is to migrate many of those to Skia suported environemnt.

Positive:
- Multi OS platform using WinForms style (if you are wpf/xaml hater :).
- Very easy to design and control UI components (even without designer tool).
- Trimming + NativeAoT support (unlike WinForms there are no COM limitations).
- Modern look and feel.
- Solid performance for CPU based rendering (Skia).
- Relatively small application size and low memory usage (but only when using single buffer modification).

Negative:
- Requires some effort (and Skia knowledge) to port WinForm controls.
- Control based buffers and re-rendering controls for each frame is not the best design choice for larger applications. I had to modify paint methods to use single buffer and render only invalidated controls. This boosted performance significantly.
- Working with separate Form objects is tricky and needs to be improved. Had to apply some tricks to achieve wanted behavior and avoid memory leaks.
- When designing or porting old WinForms controls you must pay special attention to scaling. Many old WinForms control don't have good layout functionallity, so you might loose lot of time finding ways around it.
