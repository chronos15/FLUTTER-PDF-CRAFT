// Automatic FlutterFlow imports
import '../../backend/backend.dart';
import '../../flutter_flow/flutter_flow_theme.dart';
import '../../flutter_flow/flutter_flow_util.dart';
import '../actions/index.dart'; // Imports other custom actions
import '../../flutter_flow/custom_functions.dart'; // Imports custom functions
import 'package:flutter/material.dart';
// Begin custom action code
// DO NOT REMOVE OR MODIFY THE CODE ABOVE!

import 'package:pdf/pdf.dart';
import 'package:pdf/widgets.dart' as pw;
import 'package:printing/printing.dart';
import 'dart:io';
import 'package:file_picker/file_picker.dart';

Future pdfInvoiceDownload(
  String clientname,
  String address,
  String logo,
  String amount,
  String tax,
  List<SamplesRecord> samples,
  String payment,
  String email,
  String phone,
  String sampledby,
) async {
  // Add your function code here!

  final pdf = pw.Document();
  final logoImage = await networkImage(logo);

  pdf.addPage(pw.Page(
      pageFormat: PdfPageFormat.a4.landscape,
      build: (pw.Context context) {
        return pw.Column(children: [
          pw.Text("CHAIN OF CUSTODY/ANALYSIS REQUEST",
              style: pw.TextStyle(fontSize: 15.5)),
          pw.Row(
            mainAxisAlignment: pw.MainAxisAlignment.spaceBetween,
            children: [
              pw.SizedBox(
                height: 117,
                width: 38,
                child: pw.Image(logoImage),
              ),
              pw.Column(
                children: [
                  pw.Text('1301 E. Atlantic Blvd., Suite 5',
                      style: pw.TextStyle(fontSize: 10.5)),
                  pw.Text('Pompano Beach, FL 33060',
                      style: pw.TextStyle(fontSize: 8.1)),
                  pw.Text('Phone: 954-333-8149',
                      style: pw.TextStyle(fontSize: 8.1)),
                  pw.Text('Fax:   954-333-8151',
                      style: pw.TextStyle(fontSize: 8.1)),
                  pw.Text('www.aemlinc.com',
                      style: pw.TextStyle(fontSize: 8.1)),
                ],
                crossAxisAlignment: pw.CrossAxisAlignment.start,
              ),
            ],
          ),
          pw.Container(height: 5),
          pw.Table(
            border: pw.TableBorder.all(color: PdfColors.black),
            children: [
              pw.TableRow(
                children: [
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Company:',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Sampled By:',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Payment Type:',
                      )),
                ],
              ),
              pw.TableRow(
                children: [
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Contact Name:',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Project/Site Name:',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Credit Card Type:',
                      ))
                ],
              ),
              pw.TableRow(
                children: [
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Address:',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Project #:',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Credit Card #:',
                      )),
                ],
              ),
              pw.TableRow(
                children: [
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'City:',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'State: ',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Zip: ',
                      )),
                ],
              ),
              pw.TableRow(
                children: [
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Phone #:',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Fax #:',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Signature:',
                      )),
                ],
              )
            ],
          ),
          pw.Table(
            border: pw.TableBorder.all(color: PdfColors.black),
            children: [
              // The first row just contains a phrase 'INVOICE FOR PAYMENT'
              pw.TableRow(
                children: [
                  pw.Expanded(
                    child: pw.Padding(
                      child: pw.Text(
                        ' ',
                        style: pw.Theme.of(context).header4,
                        textAlign: pw.TextAlign.center,
                      ),
                      padding: pw.EdgeInsets.all(5),
                    ),
                    flex: 1,
                  ),
                  pw.Expanded(
                    child: pw.Padding(
                      child: pw.Text(
                        'Sample Identification',
                        style: pw.Theme.of(context).header4,
                        textAlign: pw.TextAlign.center,
                      ),
                      padding: pw.EdgeInsets.all(5),
                    ),
                    flex: 2,
                  ),
                  pw.Expanded(
                    child: pw.Padding(
                      child: pw.Text(
                        'Date',
                        style: pw.Theme.of(context).header4,
                        textAlign: pw.TextAlign.center,
                      ),
                      padding: pw.EdgeInsets.all(5),
                    ),
                    flex: 1,
                  ),
                  pw.Expanded(
                    child: pw.Padding(
                      child: pw.Text(
                        'Sample Type',
                        style: pw.Theme.of(context).header4,
                        textAlign: pw.TextAlign.center,
                      ),
                      padding: pw.EdgeInsets.all(5),
                    ),
                    flex: 1,
                  ),
                  pw.Expanded(
                    child: pw.Padding(
                      child: pw.Text(
                        'Volume (Air)',
                        style: pw.Theme.of(context).header4,
                        textAlign: pw.TextAlign.center,
                      ),
                      padding: pw.EdgeInsets.all(5),
                    ),
                    flex: 1,
                  ),
                  pw.Expanded(
                    child: pw.Padding(
                      child: pw.Text(
                        'Area (Swabs)',
                        style: pw.Theme.of(context).header4,
                        textAlign: pw.TextAlign.center,
                      ),
                      padding: pw.EdgeInsets.all(5),
                    ),
                    flex: 1,
                  ),
                ],
              ),
              // The remaining rows contain each item from the invoice, and uses the
              // map operator (the ...) to include these items in the list
              ...samples.map(
                // Each new line item for the invoice should be rendered on a new TableRow
                (e) => pw.TableRow(
                  children: [
                    // We can use an Expanded widget, and use the flex parameter to specify
                    // how wide this particular widget should be. With a flex parameter of
                    // 2, the description widget will be 66% of the available width.
                    pw.Expanded(
                      child: pw.Padding(
                        padding: pw.EdgeInsets.all(5),
                        child: pw.Text(
                          '1',
                          textAlign: pw.TextAlign.left,
                        ),
                      ),
                      flex: 1,
                    ),
                    pw.Expanded(
                      child: pw.Padding(
                        padding: pw.EdgeInsets.all(5),
                        child: pw.Text(
                          e.smplLocation.toString(),
                          textAlign: pw.TextAlign.left,
                        ),
                      ),
                      flex: 2,
                    ),
                    pw.Expanded(
                      child: pw.Padding(
                        padding: pw.EdgeInsets.all(5),
                        child: pw.Text(
                          e.smplCreated!.day.toString(),
                          textAlign: pw.TextAlign.left,
                        ),
                      ),
                      flex: 1,
                    ),
                    pw.Expanded(
                      child: pw.Padding(
                        padding: pw.EdgeInsets.all(5),
                        child: pw.Text(
                          e.smplType.toString(),
                          textAlign: pw.TextAlign.left,
                        ),
                      ),
                      flex: 1,
                    ),
                    pw.Expanded(
                      child: pw.Padding(
                        padding: pw.EdgeInsets.all(5),
                        child: pw.Text(
                          e.smplVolume.toString(),
                          textAlign: pw.TextAlign.left,
                        ),
                      ),
                      flex: 1,
                    ),
                    // Again, with a flex parameter of 1, the cost widget will be 33% of the
                    // available width.
                    pw.Expanded(
                      child: pw.Padding(
                        padding: pw.EdgeInsets.all(5),
                        child: pw.Text(
                          e.smplArea.toString(),
                          textAlign: pw.TextAlign.left,
                        ),
                      ),
                      flex: 1,
                    )
                  ],
                ),
              ),
              // After the itemized breakdown of costs, show the tax amount for this invoice
              // In this case, it's just 10% of the invoice amount
              pw.TableRow(
                children: [
                  pw.Padding(
                    padding: pw.EdgeInsets.all(5),
                    child: pw.Text(
                      'TAX',
                      textAlign: pw.TextAlign.right,
                    ),
                  ),
                  pw.Padding(
                    padding: pw.EdgeInsets.all(5),
                    child: pw.Text(
                      tax,
                    ),
                  ),
                ],
              ),
              // Show the total
              pw.TableRow(
                children: [
                  pw.Padding(
                    padding: pw.EdgeInsets.all(5),
                    child: pw.Text(
                      'TOTAL',
                      textAlign: pw.TextAlign.right,
                    ),
                  ),
                  pw.Padding(
                    padding: pw.EdgeInsets.all(5),
                    child: pw.Text(
                      amount,
                    ),
                  ),
                ],
              )
            ],
          ),
          pw.Padding(
            child: pw.Text(
              "THANK YOU FOR YOUR BUSINESS!",
            ),
            padding: pw.EdgeInsets.all(20),
          ),
          pw.Text("Please save your receipt below!"),
// Create a divider that is 1 unit high and make the appearance of
// the line dashed
          pw.Divider(
            height: 1,
            borderStyle: pw.BorderStyle.dashed,
          ),
// Space out the invoice appropriately
          pw.Container(height: 20),
// Create another table with the payment details
          pw.Table(
            border: pw.TableBorder.all(color: PdfColors.black),
            children: [
              pw.TableRow(
                children: [
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Date',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Time',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Relinquished By',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Company',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Received By',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Company',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Good Condition',
                      )),
                ],
              ),
              pw.TableRow(
                children: [
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        '',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        '',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        '',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        '',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        '',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        '',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Yes          No',
                      )),
                ],
              ),
              pw.TableRow(
                children: [
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        '',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        '',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        '',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        '',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        '',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        '',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Yes          No',
                      )),
                ],
              ),
              pw.TableRow(
                children: [
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        '',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        '',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        '',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        '',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        '',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        '',
                      )),
                  pw.Padding(
                      padding: pw.EdgeInsets.all(5),
                      child: pw.Text(
                        'Yes          No',
                      )),
                ],
              ),
            ],
          ),
// Add a final instruction about how checks should be created
// Center align and italicize this text to draw the reader's attention
// to it.
          pw.Padding(
            padding: pw.EdgeInsets.all(30),
            child: pw.Text(
              'Analysis performed is subject to AEML, Inc. Standard Terms and Conditions unless otherwise specified by contract between client and AEML, Inc',
              textAlign: pw.TextAlign.center,
            ),
          )
        ]);
      })); // Page

  await Printing.layoutPdf(
      onLayout: (PdfPageFormat format) async => pdf.save());
}