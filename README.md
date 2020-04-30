# Use-OCR-Extract-data-From-Image
Agenda: Read/ Extract Data from Non Native PDF(Scanned PDF) or Native PDF and prepare Master Excel File

Need Following Major Library:

1.	Ghost Script - gs9.23
2.	Tesseract 
3.	Python – Need to install proper version compatible with Tesseract 
4.	ImageMagick
5.	OpenCV
6.	PyPDF2 (PdfFileReader)
7.	openpyxl

Let’s follow the below steps 

1.	Read the Non-native PDF

2.	Convert these PDFs into Image (make sure convert all pages into images)
Ex. 
command = 'convert -colorspace rgb -density 300 %s%s -depth 8 -strip -background white -alpha remove %s%s%s' %(path_pdf_dist,invoices_to_extract[i],path_image_converted,invoices_to_extract[i],temp_vs)


3.	Use OpenCV to enhance the image 

4.	Use below OCR code for extract string and confidence level, pass image path into temp_crop
    with PyTessBaseAPI(psm=6,oem=3,lang='eng') as api:
        try:
            api.SetImageFile(temp_crop)
            result = api.GetUTF8Text()
            result = result.strip()
            if print_ind_data == 'Y':
                print('result-1-',result)
            try:
                word_confidence=(api.AllWordConfidences())
                if print_ind_data == 'Y':
                    print('confidence-1-',word_confidence)
            except:
                average_of_confidence = 0
                if print_ind_data == 'Y':
                    print('i am at  1 error')
        except:
            pass

Note: Need to tune the psm & oem value based on the image

5.	Parse the data according to your design. 

6.	Create a master report by using openpyxl or you can use any library

You can send a mail to me pradipanand@gmail.com in case of any query. 
