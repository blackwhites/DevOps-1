```

AngularJS ��Ļ���Ϊ���� scope ģ��������һ�� watcher �������������ݷ����仯��ʱ����� view ������� watcher ������� AngularJS �����õ� watcher ��һ���ģ�

$scope.$watch('aModel', function(newValue, oldValue) {
  //update the DOM with newValue
});
���뵽 $watch() �еĵڶ���������һ���ص��������ú����� aModel ��ֵ�����仯��ʱ��ᱻ���á�

$digest ѭ���У� watchers �ᱻ��������һ�� watcher ������ʱ�� AngularJS ���� scope ģ�ͣ�����������˱仯��ô�������� watcher �Ļص������ͻᱻ���á�
��ô����һ��������� $digest ѭ������ʲôʱ���Ը��ַ�ʽ��ʼ�ģ�

```