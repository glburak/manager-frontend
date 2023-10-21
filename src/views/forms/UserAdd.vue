<template>
  <CRow>
    <CCol :xs="12">
      <CCard class="mb-4">
        <CCardHeader>
          <strong>User Public Key Import</strong>
        </CCardHeader>
        <CCardBody>
          <p class="text-medium-emphasis small">
            User seçiniz ve public keyini ekleyiniz.
          </p>
          <DocsExample href="forms/input-group.html">
            <CInputGroup>
              <CFormInput type="text" size="lg" class="mb-4" placeholder="Username" aria-label="" />
            </CInputGroup>
            <CInputGroup>
              <CFormInput type="text" size="lg" class="mb-4" placeholder="Public Key Name" aria-label="" />
            </CInputGroup>
            <CInputGroup class="mb-3">
              <CFormInput @change="publicKeyYukleme" ref="dosyaInput" id="inputGroupFile02" type="file" aria-label="Upload" />
            </CInputGroup>
            <CInputGroup class="mb-4">
              <CFormTextarea aria-label="Public keys" rows="7">{{ publicKey }}</CFormTextarea>
            </CInputGroup>
            <CButtonGroup role="group" aria-label="Basic example">
              <CButton color="success" size="lg">Import</CButton>
            </CButtonGroup>
          </DocsExample>
        </CCardBody>
      </CCard>
    </CCol>
    <CCol :xs="12">
      <CCard class="mb-4">
        <CCardHeader>
          <strong>Vue Table</strong> <small>Small tables</small>
        </CCardHeader>
        <CCardBody>
          <p class="text-medium-emphasis small">
            Add <code>small</code> property to make any
            <code>&lt;CTable&gt;</code> more compact by cutting all cell
            <code>padding</code> in half.
          </p>
          <DocsExample href="components/table.html#small-tables">
            <CTable small>
              <CTableHead>
                <CTableRow>
                  <CTableHeaderCell scope="col">#</CTableHeaderCell>
                  <CTableHeaderCell scope="col">Public key name</CTableHeaderCell>
                  <CTableHeaderCell scope="col">Expire date</CTableHeaderCell>
                </CTableRow>
              </CTableHead>
              <CTableBody>
                <CTableRow>
                  <CTableHeaderCell scope="row">1</CTableHeaderCell>
                  <CTableDataCell>Mark</CTableDataCell>
                  <CTableDataCell>Otto</CTableDataCell>
                </CTableRow>
              </CTableBody>
            </CTable>
          </DocsExample>
        </CCardBody>
      </CCard>
    </CCol>
  </CRow>
</template>

<script>
export default {
  data() {
    return {
      publicKey: "",
    }
  },
  methods: {
    publicKeyYukleme(event) {

      // Dosya yükleme işlemi başarılı olursa
      if (event.target.files.length > 0) {
        // Dosyanın içeriğini okuyun
        const file = event.target.files[0]
        const reader = new FileReader()

        reader.onload = () => {
          // Dosyanın içeriğini console'a bastırın
          this.publicKey = reader.result
        }

        reader.readAsText(file)
      }
    },
    sendPublicKey(){
      
    },
  },
  name: 'UserAdd',
}
</script>
