# Real world application example (using Modern.Forms).

### Mobile radio station performance tracker (KPI) and cluster acceptance tool (CAR). 
> Internal application used by Ericsson.  
> Application Backend: WebAPI, MediatR/Hangfire, Postgres/PostGIS db, Time series ML processing etc.  
> Purpose : anomaly detection for newly integrated Ericsson Mobile station radio units and baseband controllers.

![ericsson-logo-1-2548221570](https://github.com/dax-leo/Modern.Forms.Showcases/assets/70173560/77f7951f-7010-4754-b5a0-ff1bbcf13d21)



Components used: 
- Modern.Forms core library (with some local modifications, mostly rendering improv.).
- My own (old) datagrid component (ported from WinForms). This is something where I spent most of my time.
- ReoGrid - ported from WinForms. Partial port. Without pdf, printing and scripting - didn't need those.
- GMAP.NET - ported from WinForms - reused Winforms code + added my own WMS impelementation.
- Calendar and Calendar Drop Down component - ported from WinForms.
- ScottPlot - port to ModernForms (ScottPlot is already based on Skia hence only thin wrapper around it is needed for Modern Forms control).

### Main View
![image](https://github.com/dax-leo/Modern.Forms.Showcases/assets/70173560/f0625b10-1efa-4206-85c9-dbeec3134bc5)

### Reports with spreadsheets
![image](https://github.com/dax-leo/Modern.Forms.Showcases/assets/70173560/298e061f-ab21-4eb6-b0f4-7fd4f40173ae)

### ... some charts
![image](https://github.com/dax-leo/Modern.Forms.Showcases/assets/70173560/cffe7305-46f2-4d66-8c68-745c0e47528b)

### Popup Charts with interactive control (zoom etc.)
![image](https://github.com/dax-leo/Modern.Forms.Showcases/assets/70173560/404e24e2-1d8b-4518-b2ae-2b621e392b31)

### Complex node/time filtering
![image](https://github.com/dax-leo/Modern.Forms.Showcases/assets/70173560/b5f24c69-1ead-471b-9dc0-8cb444cd9901)


Positive:
- Multi OS platform using WinForms style (if you are wpf/xaml hater :).
- Eeasy to design and control UI components (even without designer tool).
- Trimming + NativeAoT support (unlike WinForms no need to deal with COM nightmare).
- Modern look and feel.
- Solid performance for CPU based rendering (Skia).
- Relatively small application size and low memory usage (only when using (my own) single buffer modification).

Negative:
- Requires some effort (and Skia knowledge) to port WinForm controls.
- Control based buffers and re-rendering full frame each time is not the best design choice for larger applications. I had to modify paint methods to use single buffer and render only invalidated controls. This boosted performance significantly.
- Working with separate Form objects is tricky and needs to be improved. Had to apply some tricks to achieve wanted behavior and avoid memory leaks.
- When designing or porting old WinForms controls you must pay special attention to scaling. Many old WinForms control don't have good layout functionallity, so you might loose lot of time finding ways around it.
