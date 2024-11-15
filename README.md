
# Aplikasi Penghitungan Diskon



# Deskripsi
aplikasi ini digunakan untuk menghitung harga akhir setelah diskon diterapkan. Pengguna memasukkan harga asli, memilih persentase diskon, dan jika ada, memasukkan kupon diskon. Setelah itu, tombol "Hitung" akan mengupdate harga akhir dan menunjukkan penghematan yang diperoleh.
# Features

Berikut adalah deskripsi fitur-fitur utama aplikasi ini:

1. Kolom Input:
- Harga Asli: Kolom teks untuk memasukkan harga asli barang sebelum diskon.
- Presentase Diskon: Sebuah slider yang memungkinkan pengguna untuk memilih persentase diskon yang akan diterapkan pada harga asli.

2. Kolom Hasil:
- Harga Akhir: Kolom untuk menampilkan harga barang setelah diskon diterapkan.
- Penghematan: Kolom untuk menampilkan jumlah uang yang dihemat berkat diskon yang diterapkan.
- Kupon Diskon: Kolom untuk memasukkan kode kupon diskon (jika ada), yang dapat memberikan diskon tambahan.

3. Tombol :
- Hitung: Tombol yang digunakan untuk menghitung hasil dari penghitungan diskon, yang akan memperbarui kolom "Harga Akhir" dan "Penghematan" berdasarkan input yang dimasukkan.

4. Output:
- Di bawah tombol, ada sebuah area kosong untuk menampilkan riwayat perhitungan diskon yang telah dilakukan. 
 # Source Code
 ```java
  import javax.swing.JOptionPane;
import java.awt.event.ItemEvent;



public class DiskonFrame extends javax.swing.JFrame {
        private int diskonTerakhir = 0;

    /**
     * Creates new form DiskonFrame
     */
    public DiskonFrame() {
        initComponents();
        
        kodeKuponTextField.getDocument().addDocumentListener(new javax.swing.event.DocumentListener() {
    @Override
    public void insertUpdate(javax.swing.event.DocumentEvent e) {
        hitungHargaAkhir();
    }

    @Override
    public void removeUpdate(javax.swing.event.DocumentEvent e) {
        hitungHargaAkhir();
    }

    @Override
    public void changedUpdate(javax.swing.event.DocumentEvent e) {
        hitungHargaAkhir();
    }
});

    }
    
   private void hitungHargaAkhir() {
    try {
        // Mendapatkan nilai harga asli dari TextField
        double hargaAsli = Double.parseDouble(hargaAsliTextField.getText());

        // Tahap 1: Hitung diskon utama berdasarkan diskonTerakhir
        double penghematanUtama = hargaAsli * diskonTerakhir / 100;
        double hargaSetelahDiskonUtama = hargaAsli - penghematanUtama;

        // Tahap 2: Memeriksa kode kupon untuk diskon tambahan
        String kodeKupon = kodeKuponTextField.getText().trim();
        double diskonTambahan = 0;

        // Cek kode kupon dan tentukan diskon tambahan
        if (kodeKupon.equalsIgnoreCase("DISKON5")) {
            diskonTambahan = 5;  // Diskon tambahan 5%
        } else if (kodeKupon.equalsIgnoreCase("DISKON10")) {
            diskonTambahan = 10; // Diskon tambahan 10%
        }

        // Hitung penghematan tambahan jika kode kupon valid
        double penghematanTambahan = hargaSetelahDiskonUtama * diskonTambahan / 100;
        double hargaAkhir = hargaSetelahDiskonUtama - penghematanTambahan;

        // Menampilkan hasil perhitungan pada JLabel atau JTextField
        hargaAkhirLabel.setText("Harga Akhir: Rp" + String.format("%.2f", hargaAkhir));
        penghematanLabel.setText("Penghematan: Rp" + String.format("%.2f", penghematanUtama + penghematanTambahan));

        // Menambahkan riwayat perhitungan ke JTextArea
        String riwayat = String.format(
            "Harga Asli: Rp%.2f, Diskon Utama: %d%%, Kupon: %s, Penghematan: Rp%.2f, Harga Akhir: Rp%.2f\n",
            hargaAsli, diskonTerakhir, kodeKupon, penghematanUtama + penghematanTambahan, hargaAkhir);
        riwayatTextArea.append(riwayat); // Menambahkan teks ke JTextArea

    } catch (NumberFormatException e) {
        // Kosongkan hasil jika input tidak valid
        hargaAkhirLabel.setText("Harga Akhir: Rp0.00");
        penghematanLabel.setText("Penghematan: Rp0.00");
    }
}





    /**
     * This method is called from within the constructor to initialize the form.
     * WARNING: Do NOT modify this code. The content of this method is always
     * regenerated by the Form Editor.
     */
    @SuppressWarnings("unchecked")
    // <editor-fold defaultstate="collapsed" desc="Generated Code">                          
    private void initComponents() {

        jPanel1 = new javax.swing.JPanel();
        jLabel1 = new javax.swing.JLabel();
        jLabel2 = new javax.swing.JLabel();
        jLabel3 = new javax.swing.JLabel();
        jLabel4 = new javax.swing.JLabel();
        hargaAsliTextField = new javax.swing.JTextField();
        comboBoxDiskon = new javax.swing.JComboBox<>();
        jButton1 = new javax.swing.JButton();
        hargaAkhirLabel = new javax.swing.JTextField();
        penghematanLabel = new javax.swing.JTextField();
        sliderDiskon = new javax.swing.JSlider();
        jLabel5 = new javax.swing.JLabel();
        jScrollPane1 = new javax.swing.JScrollPane();
        riwayatTextArea = new javax.swing.JTextArea();
        jLabel6 = new javax.swing.JLabel();
        kodeKuponTextField = new javax.swing.JTextField();

        setDefaultCloseOperation(javax.swing.WindowConstants.EXIT_ON_CLOSE);

        jLabel1.setText("Harga Asli");

        jLabel2.setText("Presentase Diskon");

        jLabel3.setText("Harga Akhir");

        jLabel4.setText("Penghematan");

        hargaAsliTextField.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                hargaAsliTextFieldActionPerformed(evt);
            }
        });
        hargaAsliTextField.addKeyListener(new java.awt.event.KeyAdapter() {
            public void keyTyped(java.awt.event.KeyEvent evt) {
                hargaAsliTextFieldKeyTyped(evt);
            }
        });

        comboBoxDiskon.setModel(new javax.swing.DefaultComboBoxModel<>(new String[] { "Diskon", "0%", "10%", "20%", "30%", "40%", "50%", "60%", "70%", "80%", "90%", "100%" }));
        comboBoxDiskon.setCursor(new java.awt.Cursor(java.awt.Cursor.HAND_CURSOR));
        comboBoxDiskon.addItemListener(new java.awt.event.ItemListener() {
            public void itemStateChanged(java.awt.event.ItemEvent evt) {
                comboBoxDiskonItemStateChanged(evt);
            }
        });
        comboBoxDiskon.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                comboBoxDiskonActionPerformed(evt);
            }
        });

        jButton1.setBackground(new java.awt.Color(153, 204, 255));
        jButton1.setText("Hitung");
        jButton1.setCursor(new java.awt.Cursor(java.awt.Cursor.HAND_CURSOR));
        jButton1.addChangeListener(new javax.swing.event.ChangeListener() {
            public void stateChanged(javax.swing.event.ChangeEvent evt) {
                jButton1StateChanged(evt);
            }
        });
        jButton1.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                jButton1ActionPerformed(evt);
            }
        });

        hargaAkhirLabel.setEditable(false);
        hargaAkhirLabel.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                hargaAkhirLabelActionPerformed(evt);
            }
        });

        penghematanLabel.setEditable(false);
        penghematanLabel.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                penghematanLabelActionPerformed(evt);
            }
        });

        sliderDiskon.setPaintLabels(true);
        sliderDiskon.setPaintTicks(true);
        sliderDiskon.setCursor(new java.awt.Cursor(java.awt.Cursor.HAND_CURSOR));
        sliderDiskon.addChangeListener(new javax.swing.event.ChangeListener() {
            public void stateChanged(javax.swing.event.ChangeEvent evt) {
                sliderDiskonStateChanged(evt);
            }
        });

        jLabel5.setBackground(new java.awt.Color(255, 0, 0));
        jLabel5.setFont(new java.awt.Font("Times New Roman", 1, 40)); // NOI18N
        jLabel5.setHorizontalAlignment(javax.swing.SwingConstants.CENTER);
        jLabel5.setText("Aplikasi Penghitungan Diskon ");

        riwayatTextArea.setEditable(false);
        riwayatTextArea.setColumns(20);
        riwayatTextArea.setRows(5);
        jScrollPane1.setViewportView(riwayatTextArea);

        jLabel6.setText("Kupon Diskon");

        javax.swing.GroupLayout jPanel1Layout = new javax.swing.GroupLayout(jPanel1);
        jPanel1.setLayout(jPanel1Layout);
        jPanel1Layout.setHorizontalGroup(
            jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(jPanel1Layout.createSequentialGroup()
                .addGroup(jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                    .addComponent(jLabel5, javax.swing.GroupLayout.PREFERRED_SIZE, 913, javax.swing.GroupLayout.PREFERRED_SIZE)
                    .addGroup(jPanel1Layout.createSequentialGroup()
                        .addGap(232, 232, 232)
                        .addGroup(jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                            .addGroup(jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.TRAILING)
                                .addComponent(jLabel2, javax.swing.GroupLayout.PREFERRED_SIZE, 118, javax.swing.GroupLayout.PREFERRED_SIZE)
                                .addComponent(jLabel1, javax.swing.GroupLayout.PREFERRED_SIZE, 118, javax.swing.GroupLayout.PREFERRED_SIZE)
                                .addComponent(jLabel3, javax.swing.GroupLayout.PREFERRED_SIZE, 118, javax.swing.GroupLayout.PREFERRED_SIZE)
                                .addComponent(jLabel4, javax.swing.GroupLayout.PREFERRED_SIZE, 118, javax.swing.GroupLayout.PREFERRED_SIZE))
                            .addComponent(jLabel6))
                        .addGap(44, 44, 44)
                        .addGroup(jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                            .addComponent(kodeKuponTextField, javax.swing.GroupLayout.PREFERRED_SIZE, 208, javax.swing.GroupLayout.PREFERRED_SIZE)
                            .addComponent(hargaAsliTextField, javax.swing.GroupLayout.PREFERRED_SIZE, 208, javax.swing.GroupLayout.PREFERRED_SIZE)
                            .addGroup(jPanel1Layout.createSequentialGroup()
                                .addComponent(sliderDiskon, javax.swing.GroupLayout.PREFERRED_SIZE, 137, javax.swing.GroupLayout.PREFERRED_SIZE)
                                .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                                .addComponent(comboBoxDiskon, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE))
                            .addComponent(hargaAkhirLabel, javax.swing.GroupLayout.PREFERRED_SIZE, 208, javax.swing.GroupLayout.PREFERRED_SIZE)
                            .addComponent(penghematanLabel, javax.swing.GroupLayout.PREFERRED_SIZE, 208, javax.swing.GroupLayout.PREFERRED_SIZE))))
                .addContainerGap(javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE))
            .addGroup(javax.swing.GroupLayout.Alignment.TRAILING, jPanel1Layout.createSequentialGroup()
                .addGap(0, 0, Short.MAX_VALUE)
                .addGroup(jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                    .addGroup(javax.swing.GroupLayout.Alignment.TRAILING, jPanel1Layout.createSequentialGroup()
                        .addComponent(jButton1, javax.swing.GroupLayout.PREFERRED_SIZE, 110, javax.swing.GroupLayout.PREFERRED_SIZE)
                        .addGap(368, 368, 368))
                    .addGroup(javax.swing.GroupLayout.Alignment.TRAILING, jPanel1Layout.createSequentialGroup()
                        .addComponent(jScrollPane1, javax.swing.GroupLayout.PREFERRED_SIZE, 370, javax.swing.GroupLayout.PREFERRED_SIZE)
                        .addGap(240, 240, 240))))
        );
        jPanel1Layout.setVerticalGroup(
            jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(jPanel1Layout.createSequentialGroup()
                .addComponent(jLabel5, javax.swing.GroupLayout.PREFERRED_SIZE, 66, javax.swing.GroupLayout.PREFERRED_SIZE)
                .addGap(59, 59, 59)
                .addGroup(jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.BASELINE)
                    .addComponent(jLabel1)
                    .addComponent(hargaAsliTextField, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE))
                .addGap(18, 18, 18)
                .addGroup(jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                    .addComponent(jLabel2)
                    .addComponent(sliderDiskon, javax.swing.GroupLayout.PREFERRED_SIZE, 22, javax.swing.GroupLayout.PREFERRED_SIZE)
                    .addComponent(comboBoxDiskon, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE))
                .addGap(18, 18, 18)
                .addGroup(jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                    .addComponent(jLabel3)
                    .addComponent(hargaAkhirLabel, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE))
                .addGap(18, 18, 18)
                .addGroup(jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.BASELINE)
                    .addComponent(jLabel4)
                    .addComponent(penghematanLabel, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE))
                .addGap(18, 18, 18)
                .addGroup(jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.BASELINE)
                    .addComponent(jLabel6)
                    .addComponent(kodeKuponTextField, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE))
                .addGap(18, 18, 18)
                .addComponent(jButton1)
                .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.UNRELATED)
                .addComponent(jScrollPane1, javax.swing.GroupLayout.PREFERRED_SIZE, 137, javax.swing.GroupLayout.PREFERRED_SIZE)
                .addContainerGap(28, Short.MAX_VALUE))
        );

        javax.swing.GroupLayout layout = new javax.swing.GroupLayout(getContentPane());
        getContentPane().setLayout(layout);
        layout.setHorizontalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(layout.createSequentialGroup()
                .addContainerGap()
                .addComponent(jPanel1, javax.swing.GroupLayout.PREFERRED_SIZE, 884, javax.swing.GroupLayout.PREFERRED_SIZE)
                .addContainerGap(javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE))
        );
        layout.setVerticalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addComponent(jPanel1, javax.swing.GroupLayout.Alignment.TRAILING, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE)
        );

        pack();
    }// </editor-fold>                        

    private void jButton1ActionPerformed(java.awt.event.ActionEvent evt) {                                         
            hitungHargaAkhir();    // TODO add your handling code here:
    }                                        

    private void sliderDiskonStateChanged(javax.swing.event.ChangeEvent evt) {                                          
      diskonTerakhir = sliderDiskon.getValue();
    comboBoxDiskon.setSelectedItem(diskonTerakhir + "%");  // sinkronkan JComboBox
    hitungHargaAkhir();  // panggil metode untuk menghitung harga akhir
    }                                         

    private void comboBoxDiskonActionPerformed(java.awt.event.ActionEvent evt) {                                               
                // TODO add your handling code here:
    }                                              

    private void comboBoxDiskonItemStateChanged(java.awt.event.ItemEvent evt) {                                                
        if (evt.getStateChange() == ItemEvent.SELECTED) {
        String selectedDiskon = comboBoxDiskon.getSelectedItem().toString();
        diskonTerakhir = Integer.parseInt(selectedDiskon.replace("%", ""));
        sliderDiskon.setValue(diskonTerakhir);  // sinkronkan slider
        hitungHargaAkhir();  // panggil metode untuk menghitung harga akhir
    } // TODO add your handling code here:
    }                                               

    private void hargaAkhirLabelActionPerformed(java.awt.event.ActionEvent evt) {                                                
         try {
        // Mendapatkan nilai harga asli dari TextField
        double hargaAsli = Double.parseDouble(hargaAsliTextField.getText());
        
        // Menghitung penghematan dan harga akhir berdasarkan diskonTerakhir
        double penghematan = hargaAsli * diskonTerakhir / 100;
        double hargaAkhir = hargaAsli - penghematan;

        // Menampilkan hasil perhitungan pada JLabel atau JTextField
         hargaAkhirLabel.setText("Harga Akhir: " + hargaAkhir);
         penghematanLabel.setText("Penghematan: " + penghematan);
    } catch (NumberFormatException e) {
        // Menampilkan pesan kesalahan jika input harga asli bukan angka yang valid
        JOptionPane.showMessageDialog(this, "Masukkan angka valid untuk harga asli.", "Error", JOptionPane.ERROR_MESSAGE);
    }                // TODO add your handling code here:
    }                                               

    private void jButton1StateChanged(javax.swing.event.ChangeEvent evt) {                                      
        // TODO add your handling code here:
    }                                     

    private void penghematanLabelActionPerformed(java.awt.event.ActionEvent evt) {                                                 
        // TODO add your handling code here:
    }                                                

    private void hargaAsliTextFieldActionPerformed(java.awt.event.ActionEvent evt) {                                                   
        // TODO add your handling code here:
    }                                                  

    private void hargaAsliTextFieldKeyTyped(java.awt.event.KeyEvent evt) {                                            
         char input = evt.getKeyChar();
    if(!Character.isDigit(input)){
        evt.consume(); // Hanya angka yang diperbolehkan
    }        // TODO add your handling code here:
    }                                           

    /**
     * @param args the command line arguments
     */
    public static void main(String args[]) {
        /* Set the Nimbus look and feel */
        //<editor-fold defaultstate="collapsed" desc=" Look and feel setting code (optional) ">
        /* If Nimbus (introduced in Java SE 6) is not available, stay with the default look and feel.
         * For details see http://download.oracle.com/javase/tutorial/uiswing/lookandfeel/plaf.html 
         */
        try {
            for (javax.swing.UIManager.LookAndFeelInfo info : javax.swing.UIManager.getInstalledLookAndFeels()) {
                if ("Nimbus".equals(info.getName())) {
                    javax.swing.UIManager.setLookAndFeel(info.getClassName());
                    break;
                }
            }
        } catch (ClassNotFoundException ex) {
            java.util.logging.Logger.getLogger(DiskonFrame.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (InstantiationException ex) {
            java.util.logging.Logger.getLogger(DiskonFrame.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (IllegalAccessException ex) {
            java.util.logging.Logger.getLogger(DiskonFrame.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (javax.swing.UnsupportedLookAndFeelException ex) {
            java.util.logging.Logger.getLogger(DiskonFrame.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        }
        //</editor-fold>

        /* Create and display the form */
        java.awt.EventQueue.invokeLater(new Runnable() {
            public void run() {
                new DiskonFrame().setVisible(true);
            }
        });
    }

    // Variables declaration - do not modify                     
    private javax.swing.JComboBox<String> comboBoxDiskon;
    private javax.swing.JTextField hargaAkhirLabel;
    private javax.swing.JTextField hargaAsliTextField;
    private javax.swing.JButton jButton1;
    private javax.swing.JLabel jLabel1;
    private javax.swing.JLabel jLabel2;
    private javax.swing.JLabel jLabel3;
    private javax.swing.JLabel jLabel4;
    private javax.swing.JLabel jLabel5;
    private javax.swing.JLabel jLabel6;
    private javax.swing.JPanel jPanel1;
    private javax.swing.JScrollPane jScrollPane1;
    private javax.swing.JTextField kodeKuponTextField;
    private javax.swing.JTextField penghematanLabel;
    private javax.swing.JTextArea riwayatTextArea;
    private javax.swing.JSlider sliderDiskon;
    // End of variables declaration                   
}


```




# Authors

- MuhammadSaputraArjunaidy
- 2210010300
- 5B Reg Pagi Banjarmasin
- [@MuhammadSaputraArjunaidy](https://www.github.com/MuhammadSaputraArjunaidy)


#  Screenshot