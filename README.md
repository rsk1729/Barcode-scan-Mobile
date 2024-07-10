<%@ Page Language="C#" AutoEventWireup="true" CodeFile="BarcodeDemo.aspx.cs" Inherits="Production_BarcodeDemo" %>

    <!DOCTYPE html>

    <html xmlns="http://www.w3.org/1999/xhtml">

    <head id="Head1" runat="server">
        <title></title>

        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" />
        <!-- Font Awesome CSS -->
        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css" />
            <script src="PRD_Scripts/BarcodeDemo.js"></script>
            <style>
                #my-qr-reader {
                    padding: 20px !important;
                    border: 1.5px solid #b2b2b2 !important;
                    border-radius: 8px;
                }

                #my-qr-reader img[alt="Info icon"] {
                    display: none;
                }

                #my-qr-reader img[alt="Camera based scan"] {
                    width: 100px !important;
                    height: 100px !important;
                }


                button {
                    padding: 10px 20px;
                    border: 1px solid #b2b2b2;
                    outline: none;
                    border-radius: 0.25em;
                    color: white;
                    font-size: 15px;
                    cursor: pointer;
                    margin-top: 15px;
                    margin-bottom: 10px;
                    background-color: #008000ad;
                    transition: 0.3s background-color;
                }

                button:hover {
                    background-color: #008000;
                }

                #html5-qrcode-anchor-scan-type-change {
                    text-decoration: none !important;
                    color: #1d9bf0;
                }

                video {
                    width: 100% !important;
                    border: 1px solid #b2b2b2 !important;
                    border-radius: 0.25em;
                }

                .row {
                    margin-left: 0px !important;
                    margin-right: 0px !important;
                }

                .container-fluid {
                    background-color: #096a8a;
                }

                .headerRow {
                    background-color: #096a8a;
                    padding: 10px;
                    width: 100%;
                }

                .headerRow label {
                    color: #fff;
                    font-size: 14px;
                    font-weight: 700;
                }

                .fa-pencil-square-o {
                    color: rgb(247, 126, 28);
                }

                #tblPrdnView>thead>tr>th {
                    vertical-align: middle;
                    background-color: #333;
                    border: 1px solid #000000;
                    color: #fff;
                    font-size: 14px;
                    text-align: center;
                }

                #tblPrdnView>tbody>tr>td {
                    background-color: #ffffff;
                    color: #333;
                    border-bottom: 1px solid #194961 !important;
                    font-size: 12px;
                    border: 1px solid;
                    font-weight: 700;
                }

                /* Modal styles */
                .modal {
                    display: none;
                    position: fixed;
                    z-index: 1;
                    left: 0;
                    top: 0;
                    width: 100%;
                    height: 100%;
                    overflow: auto;
                    background-color: rgba(0, 0, 0, 0.4);
                }

                .modal-content {
                    background-color: #fefefe;
                    margin: 5% auto;
                    padding: 20px;
                    border: 1px solid #888;
                    width: 80%;
                    max-width: 500px;
                    height: -webkit-fill-available;
                }

                .close {
                    color: #aaa;
                    float: right;
                    font-size: 28px;
                    font-weight: bold;
                }

                .close:hover,
                .close:focus {
                    color: black;
                    text-decoration: none;
                    cursor: pointer;
                }

                .modal1 {
                    display: none;
                    position: fixed;
                    z-index: 1;
                    left: 0;
                    top: 0;
                    width: 100%;
                    height: 100%;
                    overflow: auto;
                    background-color: rgba(0, 0, 0, 0.4);
                }

                .modal1-content {
                    background-color: #fefefe;
                    margin: 5% auto;
                    padding: 20px;
                    border: 1px solid #888;
                    width: 80%;
                    max-width: 400px;
                }

            
                .result {
                    background-color: #4caccd;
                    padding: 10px;
                    margin-top: 20px;
                    text-align: center;
                }


                .fa-camera {
                    font-size: 28px;
                    color: floralwhite;
                    cursor: pointer;
                }

                #tblPrdnView tr:hover td {
                    background: #4E5066;
                    color: #FFFFFF;
                    border-top: 1px solid #22262e;
                }

                #tblPrdnView tr:nth-child(odd) td {
                    background: #EBEBEB;
                    cursor: pointer;
                }

                #tblPrdnView tr:nth-child(odd):hover td {
                    background: #4E5066;
                }

                .table-fill tr>td {
                    border: 1px solid;
                }

                .table-fill {
                    width: 100%;
                    margin-top: 10px;
                    box-shadow: 2px 2px 4px 1px #999696;
                    background: azure;
                }

                .model-header label {
                    font-size: 22px;
                    position: absolute;
                    color: darkred;
                    font-weight: 600;
                    text-align: center;
                    width: 100%;
                }

                .btnLbl {
                    width: 55px;
                    text-align: center;
                    background: #0a551b;
                    color: #fff;
                    margin-top: 10px;
                    border: 1px solid;
                    cursor: pointer;
                }

                .btnLbl:hover {
                    background: #FFFFFF;
                    color: #0a551b;
                    border: 1px solid #0a551b;
                }

                #numberInput {
                    width: 100px;
                    height: 25px;
                    position: relative;
                }

                .txtbox {
                    width: 90px;
                    height: 25px;
                    position: relative;
                    top: 10px;
                }

                .rowLbl {
                    width: 100%;
                    display: block;
                }

                .secondRow {
                    width: 100%;
                    display: block;
                }

                .btnUpdate {
                    background: #06917f;
                    color: #fff;
                    border: 1px solid #4c7900;
                    height: 25px;
                    font-size: 14px;
                    padding: 0px 10px 0px 10px;
                }

                .btnUpdate:hover {
                    background: #fff;
                    color: #06917f;
                    border: 1px solid #06917f;
                }

                .thirdRow {
                    width: 100%;
                    display: block;
                }

                .thirdRow label {
                    position: relative;
                    top: 13px;
                    padding-right: 20px;
                }

                .thirdRow input {
                    width: 50px;
                }

                #productionButton {
                    background: #009ecf;
                    color: #fff;
                    border: 1px solid #312626;
                    padding: 0 15px;
                    margin-top: 10px;
                }

                #transferButton {
                    background: #009ecf;
                    color: #fff;
                    border: 1px solid #312626;
                    padding: 0 15px;
                    margin-left: 10px;
                    margin-top: 10px;
                }

                .active {
                    background-color: #432eff !important;
                    color: #fff;
                }

                .tTime label {
                    display: block;
                    border-radius: 10px;
                    font-size: 13px;
                    background: #005f6f;
                    color: #fff;
                    margin-top: 20px;
                    text-align: center;
                }
            </style>
    </head>

    <body>
        <form id="form1" runat="server">
        
        <div class="row">
            <div class="col-md-12 col-sm-12">
                <div class="row">
              
                        <table  class="table table-bordered table-responsive table-sm" style="width: 100%!important;">
                            <thead>
                                <tr>
                                    <th>STAGE</th>
                                    <th>Planned</th>
                                    <th>Produced</th>
                                    <th>Produced Balance</th>
                                    <th>Transfer Qty</th>
                                    <th>Transfer Balance</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr class="odd" onclick="openModal()">
                                    <td>STRAP CUTTING</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                </tr>
                                <tr class="even">
                                    <td>COUPLING AND TRIMMING</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                </tr>
                                <tr class="odd">
                                    <td>SIZE CUTTING</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                </tr>
                                <tr class="even">
                                    <td>INKING AND COLORING</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                </tr>
                                <tr class="odd">
                                    <td>FINISHING - 1</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                </tr>
                                <tr class="even">
                                    <td>PACKING</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                </tr>
                                <tr class="odd">
                                    <td>ASP-02-(SUB PROCESS)</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                </tr>
                                <tr  class="even">
                                    <td>REJECTION - REWORK</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    <td class=" text-center">0</td>
                                    </tr>
                            </tbody>
                        </table>
           
                </div>

            </div>
        </div>

        <div id="modal" class="modal">
            <!-- Modal content -->

            <div class="modal-content">

                <div class="model-header">
                    <label>STRAP CUTTING</label>
                    <span class="close" onclick="closeModal()">&times;</span>
                </div>

                <div class="result">
                    <i class="fa fa-camera" aria-hidden="true" onclick="openModal1a()"></i>

                    <input id="barcodeResult" type="text" style="color: #000000;" />
                    <!-- <select id="barcodeResultSelect barcodeResult" style="color: #000000;"></select> -->
                    <input type="button" value="OK" />
                </div>

            </div>
        </div>
        <div id="modal1" class="modal1">
            <!-- Modal content -->
            <div class="modal1-content">
                <span class="close" onclick="closeModal1()">&times;</span>
                <div class="section">
                    <div id="my-qr-reader">
                    </div>
                </div>
            </div>
        </div>
</form>

        <script src="../Scripts/html5-qrcode.min.js"></script>

        <script type="text/javascript">

            function openModal() {
                document.getElementById("modal").style.display = "block";
            }

            function closeModal() {
                document.getElementById("modal").style.display = "none";
            }

            function openModal1a() {
                document.getElementById("modal1").style.display = "block";
                // startBarcodeScanner();
            }

            function closeModal1() {
                document.getElementById('modal1').style.display = 'none';
            }


            function domReady(fn) {
                if (
                    document.readyState === "complete" ||
                    document.readyState === "interactive"
                ) {
                    setTimeout(fn, 1000);
                } else {
                    document.addEventListener("DOMContentLoaded", fn);
                }
            }

            
              //////bar code scan script///

            domReady(function () {

                // If found you qr code
                function onScanSuccess(decodeText, decodeResult) {
                    document.getElementById('barcodeResult').value = decodeText;
                    closeModal1(); // Close the modal after successful scan
                }

                let htmlscanner = new Html5QrcodeScanner(
                    "my-qr-reader",
                    { fps: 10, qrbos: 250 }
                );
                htmlscanner.render(onScanSuccess);
            });


        </script>
    </body>

    </html>
