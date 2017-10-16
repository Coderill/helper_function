# helper_function
Helper function

```php

/*Maruf hasan's Helper*/
    function custom_fetch($var,$field){
        if ($var!=null) {
            return $var[0]->$field;
        }
    }

    function image($link){
        if ($link==null) {
            return site_url("private/images/placeholder.png");
        }else{
            return site_url($link);
        }
    }
    
    function filter($value){
        $capitalize="";
        $rmv_scor=str_replace("_"," ", $value);
        if (mb_detect_encoding($rmv_scor)!='UTF-8') {
            $capitalize=ucwords($rmv_scor);
        }else{
            $capitalize=$rmv_scor;
        }
        
        return $capitalize;
    }



function view_more($string,$amount,$link=null,$text="View More"){
        $strings=explode(" ", $string);

        if (count($strings)<=$amount) {
            return(implode(" ",$strings));
        }
        else{
            $out_string=array();
            for ($i=0; $i<$amount; $i++) { 
                $out_string[]=$strings[$i];
            }
            $final=implode(" ",$out_string).'<div class="view_more"> <a href="'.$link.'">'.$text.'</a> </div>';
               return($final);
        }
}

function message_length($strlength){
	$messLen = 0;
	if( $strlength <= 160){ $messLen = 1; } 
	else if( $strlength <= 306){ $messLen = 2; } 
	else if( $strlength <= 459){ $messLen = 3; } 
	else if( $strlength <= 612){ $messLen = 4; }
	else if( $strlength <= 765){ $messLen = 5; }
	else if( $strlength <= 918){ $messLen = 6; }
	else if( $strlength <= 1071){ $messLen = 7; }
	else if( $strlength <= 1080){ $messLen = 8; }
	else { $messLen = "Equal to an MMS."; }
	return $messLen;
}
//Function for Dynamic Language Start
function caption($index){
    $CI = & get_instance();
    // load model
    $CI->load->model('action');
    // use model method
    $val = $CI->action->read('site_meta',array('meta_key'=>'language'));

    $label_lang = config_item('label_lang');

    return $label_lang[$index][$val[0]->meta_value];
}
//Function for Dynamic Language End

//Function updating site information
function site_update(){
    $CI = & get_instance();
    // load model
    $CI->load->model('action');
    // use model method
    $data = array(
        'meta_value' => date('Y-m-d H:i:s a')
    );
    $where = array(
        'meta_key' => 'update_date'
    );
    $CI->action->update('site_meta',$data,$where);
}
//Function updating site information

//Array Differance
function arrayDiff($a,$b){
	$c = array_diff($a, $b);
	$d = array_diff($b, $a);
	$e = array_merge($c,$d);
	$f = array_unique($e);
	return $f;
}
//Array Differance

    function selected($v1,$v2){
        if($v1==$v2){
            echo "selected";
        }
    }

    function checked($v1,$v2){
        if($v1==$v2){
            echo "checked";
        }
    }

    function valid_equal($v1,$v2){
        if($v1==$v2){
            return true;
        }
        return false;
    }
```
