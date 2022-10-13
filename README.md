
<?php
public function test_id(){
    $check = array();
    $sql1 = "SELECT DATE(date) as date FROM table_name";
    $res1 = $this->db->query($sql1)->result();
    foreach($res1 as $k => $val)
    {
        $val_brk = explode('-',$val->date);
        $check[$k] = $val_brk[2];
            if($k != 0){
                if((int)($check[$k])-(int)($check[$k-1]) != 1){
                    $sql = "INSERT INTO table_name(date) VALUE(
                        $val_brk[2]".'/'."$val_brk[1]".'/'."$val_brk[0]
                    )";
                    $this->db->query($sql);
                }
            }
        }
        return;
    }
?>
